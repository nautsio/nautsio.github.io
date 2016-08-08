---
layout: post
title: "Looking back on Dutch Docker Day 2015"
author: Rik Farenhorst
date: 2016-02-20 08:41
cover: /img/nauts-bg.png
preview: /img/nauts-bg.png
categories:
  - article
comments: true
tags:
  - docker
  - dutchdockerday
  - workshop
  - event
  - xebia
  - container
  - talk
---
2015 was a year in which we at [Xebia](https://www.xebia.com) dived into the [Docker](https://www.docker.com) ecosystem. We helped customers in building next-gen container-based platforms, organized various meetups, and experimented a lot with various tools and technology, did shootouts, wrote opinionated blogs, organized open kitchens and, last but not least, had loads of fun in understanding all intricacies of the glue that forms contemporary container-based cloud platforms.

After Summer we decided it was imperative to share all our experiences and knowledge of the fast growing Docker ecosystem with our community. Enter [Dutch Docker Day](http://www.dutchdockerday.nl). We wanted this event to be something unique, and gathered with the whole team for a kickoff in which we outlined the experience we wanted visitors to get. We arrived at a concept in which a few core principles stood central:

- **Dive deeply**: go beyond the Hello World stage of the Docker ecosystem
- **Learn by doing**: bring your laptop: the day is packed with workshops and labs
- **Discuss with peers**: debate and share your experiences at our knowledge plaza

<div>
  <img src="/img/2016-02-20-looking-back-on-dutch-docker-day-2015/ddd-tetris.jpg" />
</div>

The event surpassed our expectations. Around 300 Docker believers gathered in the Zuiderkerk in Amsterdam to practice what we and they preach, to share knowledge and to deep dive themselves into the ecosystem. The concept of continuous food, plenty of discussion and workshop spaces, and the non-corporate atmosphere worked out quite well. In addition, our high evaluation scores were mostly dictated by the quality delivered through workshops and talks.

### Workshops
There were hands-on workshops covering a large part of the ecosystem, where attendees could learn, experiment and discuss with peers about subjects such as Docker, service discovery, schedulers, scalability and contributing to the ecosystem.

- Official Docker hands-on labs
- [Service discovery with Consul](http://nauts.io/workshop-docker-consul/)
- [Scheduling containers and more with Nomad](http://nauts.io/workshop-nomad)
- [Scaling Docker with Swarm and Compose](http://nauts.io/workshop-swarm)
- [Scalable QA with Docker](http://bit.ly/slides-scale-qa)
- [High available Docker platform using CoreOS and Consul](http://nauts.io/workshop-docker-coreos-and-consul)
- [Customizing Docker with plugins](http://nauts.io/workshop-docker-plugins)

### Talks
All through the day there were some amazing talks given on the full spectrum of the Docker ecosystem.

- #### Dutch Docker Day 2015, The opening and welcome
I opened the conference and talked about Xebia and the unique format of the Dutch Docker Day. Mark van Holsteijn then talked about New IT and Docker’s role in it.   
[Watch the video](/videos/2016/02/09/dutchdockerday-opening-and-welcome/)   
[View the slides](http://www.slideshare.net/xebia/opening-welcome-dutch-docker-day)

- #### How Docker is changing the world for development and operations
In his talk Iain Gray of Docker shared Docker’s vision on how next generation datacenters change the way both development and operations work in practice. Iain also shared the latest Docker trends and updates from Docker’s product roadmap as presented earlier that week during DockerCon Europe in Barcelona.   
[Watch the video](/videos/2016/02/09/how-docker-is-changing-the-world-for-devops/)   
[View the slides](http://www.slideshare.net/xebia/dutch-docker-day-how-docker-is-changing-the-world-for-development-and-operations)

- #### Yes, you can run full stack containers!
The current dogma about using Docker is that a container should run a single process and fulfill a single task. Thomas Kruitbosch and Eric Nieuwenhuijsen shared their experience in using Docker containers as a complete virtual machine running web servers, applications and even the MySQL database in a single container!   
[Watch the video](/videos/2016/02/09/yes-you-can-run-full-stack-containers/)   
[View the slides](http://www.slideshare.net/xebia/dutch-docker-day-yes-you-can-run-full-stack-containers)

- #### The new world of Docker multi-host networking
Docker 1.9 introduced a new networking architecture that uses VXLAN overlays to connect distinct Docker hosts. Nicola Kabar went over the new architecture, it’s advantages, and use-cases, and demoed how it can enable scaling applications with Compose and Swarm.   
[Watch the video](/videos/2016/02/09/the-new-world-of-docker-multihost-networking/)   
[View the slides](http://www.slideshare.net/xebia/dutch-docker-day-the-new-world-of-docker-multihost-networking)

- #### Dockerize your development workstation
Armin Coralic, shared all the practical examples of how he uses Docker in his day-to-day work as a full stack developer to ease his life and save loads of time!   
[Watch the video](/videos/2016/02/09/dockerize-your-development-workstation/)

- #### Docker Swarm on Kubernetes
Kelsey Hightower showed in this talk the inter-workings of Docker Swarm and how Kubernetes can be leveraged for advanced container management and orchestration through live demonstrations and story telling.   
[Watch the video](/videos/2016/02/09/docker-swarm-on-kubernetes/)

- #### Pipeline automation using Vagrant, Ansible, Docker, Swarm and Consul
Docker is taking the infrastructure world by storm, but what about the business justification for Docker? Michiel Sens explained an automated Software Delivery Pipeline using Vagrant, Ansible, Docker, Swarm, Consul and Jenkins that can help you demonstrate the advantages to your management.   
[Watch the video](/videos/2016/02/09/pipeline-automation-using-vagrant-ansible-docker-swarm-and-consul/)   
[View the slides](http://www.slideshare.net/xebia/dutch-docker-day-2015-pipeline-automation-using-vagrant-ansible-docker-swarm-consul-and-jenkins)

- #### Run your dockerized ASP.net applications on Windows and Linux
In this innovative talk, Alex and René give a quick overview of the endless possibilities of Docker on Windows and Linux in combination with ASP.NET 5.   
[Watch the video](/videos/2016/02/09/run-your-dockerized-applications-on-windows-and-linux/)   
[View the slides](http://www.slideshare.net/xebia/dutch-docker-day-2015-run-your-dockerized-aspnet-applications-on-windows-and-linux)

- #### Mesos in a moment
Joyent’s Casey Bisson demonstrates Mesos running in a public cloud on bare metal and scaling containerized workloads across multiple data centers — and prove why container-native is the future of the data center.   
[Watch the video](/videos/2016/02/09/mesos-in-a-moment/)   
[View the slides](http://www.slideshare.net/xebia/dutch-docker-day-2015-mesos-in-a-moment)

- #### Bootstrapping your Docker platform with Terraform
Docker has been a huge enabler for "immutable" applications that are easy to build, easy to deploy, and easy to replace. The underlying infrastructure to run these containerized applications seems to be much more complex. Benny Cornelissen showed us how we can codify this infrastructure, version control it, and enable rapid deployments of multiple instances of these container platforms, all in one go.   
*Link coming soon*

- #### Building self-describing microservices with Docker labels
Bas Tichelaar and Age Mooij showed why Docker labels are the perfect place to store build-time metadata, how they wrote a simple command line deployment tool that uses such metadata to generate Marathon app descriptors at deployment time, and how they customized their build tool to support all this.   
*Link coming soon*

- #### Scheduling Applications at Scale
Armon Dadgar showed us how to use Nomad to schedule diverse workloads in the modern datacenter. Nomad handles many types of workloads, on a variety of operating systems, at massive scale, and empowers developers to specify jobs and tasks using a high-level specification. Nomad accepts the job specification, determines compatible hosts, and then automatically manages the placement, healing, and scaling of the application.   
*Link coming soon*

<br/>
<div>
  <img src="/img/2016-02-20-looking-back-on-dutch-docker-day-2015/ddd-ambience.jpg" />
</div>


All in all, it was an awesome event, and I am proud to work with a team full of Docker advocates who turned out to be experienced event organizers as well. See you all next year!
