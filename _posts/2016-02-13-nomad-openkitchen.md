---
layout: post
title: "Nomad Open Kitchen"
author: Erik Veld
date: 2016-02-13
cover: /img/2016-02-08-nomad-openkitchen/nomad.png
preview: /img/2016-02-08-nomad-openkitchen/nomad.png
categories:
  - article
comments: true
tags:
  - docker
  - consul
  - hashicorp
  - nomad
  - workshop
  - event
  - sysdig
  - google
  - gce
---
For the Nomad Open Kitchen event we set out to create a reusable cloud setup that we could use to easily and repeatably create environments for attendees of our events. In this post we will share our setup and some problems we ran in to while creating it.

After having created a workshop for the [Dutch Docker Day back in November](http://www.dutchdockerday.nl), we wanted to dive deeper into what [Nomad](http://www.nomadproject.io) could offer us. We decided to start working on a new workshop, where we could mitigate some of the logistics problems we ran into when hosting our previous workshop and explore more of Nomad's features. One of the things we ran in to is that Vagrant boxes take quite a bit of bandwidth and time to be distributed to all attendees. And when they finally are distributed the differences in local environments, such as hardware, operating systems and the versions of required software, can cause a lot of headaches.

<div><img title="Dutch Docker Day" src="/img/2016-02-08-nomad-openkitchen/dutchdockerday.png" /></div>

For our next version of the workshop we wanted to host the entire setup in the cloud, it had to be light on network usage and be quick to set up on the fly for all attendees. It was also a nice opportunity to gain some more knowledge on a different cloud provider than AWS, and therefor the choice of hosting it fell on [Google Cloud](http://cloud.google.com). What we came up with is a setup that can create separate environments for each attendee repeatably and with great ease. And once it's done, it send the details of the environment to the corresponding attendee.

The first steps of creating the setup is a bit cumbersome, as we have to give terraform access to create, update and destroy resources on Google Cloud, and for that it needs to have API access (API, Google Compute Engine, Enable API) and account details (Permissions, Service accounts, Create Account, Download the credentials as JSON). These steps need to be repeated for each project.

We try to loosely simulate a production environment, with some compromises in order to cut costs. The Nomad servers run in a quorum 3 on separate machines each in a different availability zone, with one of the cost cutting choices being that the Consul quorum of 3 also runs on these 3 machines. The applications run in 2 autoscaling farms, in different availability zones. The Nomad clients are running on these farm nodes, as well as the Consul agent for service discovery.

The Consul server and clients run as a system job with the Docker driver, targeting separate datacenters, sys1 and dc1 respectively, for the server and client agents. Just by setting the constraint for each of the task groups, we can deploy them with one Nomad job, after which Nomad will automatically detect the presence of Consul and start registering it's allocations in Consul. Each stack that is created has it's own internal and external zone, so most configuration can be done based on DNS instead of IPs.

```json
job "consul" {
	datacenters = ["sys1", "dc1"]
	type = "system"

	group "server" {
		constraint {
			attribute = "$node.datacenter"
			value = "sys1"
		}

		task "consul-server" {
			driver = "docker"
			config {
				image = "gliderlabs/consul-server:latest"
				network_mode="host"
				command = "-advertise"
				args=["$network.ip-address",
				"-retry-join", "default-nomad-01",
				"-retry-join", "default-nomad-02",
				"-retry-join", "default-nomad-03",
				"-server",
				"-bootstrap-expect", "3"]
			}
		}
	}

	group "client" {
		constraint {
			attribute = "$node.datacenter"
			value = "dc1"
		}

		task "consul-client" {
			driver = "docker"
			config {
				image = "gliderlabs/consul-agent:latest"
				network_mode="host"
				command = "-advertise"
				args=["$network.ip-address",
				"-retry-join", "default-nomad-01",
				"-retry-join", "default-nomad-02",
				"-retry-join", "default-nomad-03"]
			}
		}
	}
}
```

The autoscaling farms are configured in such a way that when the load exceeds 75%, the farm will scale up automatically and the Nomad clients join the cluster and start accepting jobs and registering them in Consul.

To monitor the setup and see what all our components are doing we decided to run [Sysdig](https://www.sysdig.com) on each of the nodes and it is another job we can schedule with the Nomad system scheduler. Unfortunately we can't run it with the Docker task driver, as Sysdig needs a lot of privileges and volumes mounted in order to get all of it's information about a system. We therefor run it with the raw-exec driver, that executes the docker run command with all the needed parameters.

<div><img title="Check performance with sysdig" src="/img/2016-02-08-nomad-openkitchen/sysdig.png" /></div>

With the development of all the tools moving so rapidly, there is always the danger of things breaking when you least want it, which we experienced multiple times when creating this setup. There were some small changes in syntax and required values within the Nomad jobs that we encountered when running the 3.0-dev version, which is understandable since it's a development version, which made previously working jobs invalid.

```json
 - attribute = "$attr.kernel.name"
 + attribute = "${attr.kernel.name}"
```

A more annoying problem we ran in to was with the [Gliderlabs image](https://hub.docker.com/r/gliderlabs/consul-server/) of Consul which is updated to patch versions, but these changes are not reflected in the docker image tag. We were therefor suddenly running a patch release which changed the way consul sets it's advertise IP, and the only way to configure the docker image is by mounting a volume with the configuration, which isn't possible with Nomad. We had to change the way we deployed Consul and eventually chose to add it into the packer build, to avoid any further problems.

Although we had some more bumps in the road leading up to the [Nomad Open Kitchen](https://xebia.com/events/open-kitchen-managing-scalable-docker-container-platforms-with-nomad) event at the end of January, such as running out of resources in our Google Cloud project just before the event (oops!), the event was a success and the setup worked perfectly. The next steps are to make the setup even more flexible so it can be used for other workshops in the future and to expand it with components such as Vault for secrets management and when possible (please hurry up cloud providers) switch to IPV6 and provide each container with an IP address.

If you wish to check out the setup and view the [slides](https://www.github.com/nautsio/nomad-ok/tree/master/slides), head over to [github](https://www.github.com/nautsio/nomad-ok).
