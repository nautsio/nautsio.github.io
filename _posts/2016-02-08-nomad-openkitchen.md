---
layout: post
title: "Nomad Open Kitchen"
author: Erik Veld
date: 2016-02-08
cover: /img/nomad.png
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
After having created a workshop for the Dutch Docker Day back in November, we wanted to dive deeper into what Nomad could offer us. We decided to start working on a new workshop, where we could mitigate some of the logistics problems we ran into when hosting our previous workshop and explore more of Nomad's features. One of the things we ran in to is that Vagrant boxes take quite a bit of bandwidth and time to be distributed to all attendees. And when they finally are distributed the differences in local environments, such as hardware, operating systems and the versions of required software, can cause a lot of headaches.

<div><img title="Dutch Docker Day workshop area" src="/img/2016-02-08-nomad-openkitchen/dutchdockerday.png" /></div>

For our next version of the workshop we wanted to host the entire setup in the cloud, it had to be light on network usage and be quick to set up on the fly for all attendees. We also thought it was a nice opportunity to gain some more knowledge on a different cloud provider than AWS, and therefor wanted to host it on Google Cloud. What we came up with is a setup that can create separate environments for each attendee repeatably and with great ease. And once it's done send the details of the environment to the corresponding attendee.

The first steps of creating the setup was a bit cumbersome, as we had to give terraform access to create, update and destroy resources on Google Cloud, and for that it needed to have API access (API, Google Compute Engine, Enable API) and account details (Permissions, Service accounts, Create Account, Download the credentials as JSON). These steps need to be repeated for each project.

<div><img title="Set up google cloud credentials and api" src="/img/2016-02-08-nomad-openkitchen/googlecloud-credentials.png" /></div>

- the initial design
  - 3 nomad server nodes in a seperate datacenter
  - nomad servers configured to find eachother via dns (nomad-01, nomad-02, nomad-03)
  - nomad clients in a farm
  - the nomad client farms are in 2 availability zones to see how nomad would handle that
  - initially deployed consul with one job on both clients and servers via nomad
The Consul Server and Clients were run with the Docker driver as a system job, targeting separate datacenters, sys1 and dc1 respectively, for the Server and Client agents. Just by setting the constraint for each of the task groups, we could deploy them with one Nomad job, after which Nomad would automatically detect the presense of Consul and start registering it's allocations in Consul.
Each stack that is created has it's own internal and external zone, so most configuration can be done based on DNS instead of IPs.

- new things in 0.3-dev and incompatibility
  - some small changes in the syntax/fields of the job configuration break jobs

- problems with sysdig
  - could not be run as a system docker job because it needed volumes to be mounted which was not possible with Nomad

- problems with consul (gliderlabs versioning)
  - gliderlabs updates their images to patch versions, but does not reflect these changes in the docker image tags
  - this broke some things in the consul deployment
  - in a patch version they changed the way consul grabbed it's advertise ip
  - you cant inject configuration, unless you mount it as volume

- next steps to make it full featured (vault, ipv6, separate consul, coreos, systemd)
  - manage secrets with vault
  - give each container it's own ipv6 ip
  - run consul servers on their own nodes and let them also be the HA backend for vault
  - use sql as secrets backend for vault
