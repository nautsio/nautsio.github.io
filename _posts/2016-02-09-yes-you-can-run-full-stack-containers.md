---
layout: post
title: "Yes, you can run full stack containers!"
author: Erik Veld
date: 2016-02-09 10:45
cover: /img/2016-02-09-yes-you-can-run-full-stack-containers/fullstack-video.png
categories:
  - videos
comments: true
tags:
  - docker
  - dutchdockerday
  - event
  - talk
---
The current dogma about using Docker is that a container should run a single process and fulfill a single task. In this [talk](http://www.slideshare.net/xebia/dutch-docker-day-yes-you-can-run-full-stack-containers), Thomas Kruitbosch and Eric Nieuwenhuijsen share their experience in using Docker containers as a complete virtual machine running web servers, applications and even the MySQL database in a single container!

They describe how they used Docker virtual machines as the binary artifact that moves through a build pipeline for each feature branch as it was the fastest way to move a traditional development process to a state of the art Continuous Delivery pipeline.

<iframe
  width="960"
  height="540"
  src="http://www.youtube.com/embed/XSWGx31vwVI"
  frameborder="0"
  allowfullscreen>
</iframe>
