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


- first experiences with gce (setting up was a hassle)
- the initial design
- new things in 0.3-dev and incompatibility
- problems with sysdig
- problems with consul (gliderlabs versioning)


- next steps to make it full featured (vault, ipv6, separate consul, coreos, systemd)
