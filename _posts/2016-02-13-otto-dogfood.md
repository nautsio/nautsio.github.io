---
layout: post
title: "Otto Dog Food"
author: Bastiaan Bakker
date: 2016-02-13
cover: /img/2016-02-08-otto-dogfood/otto-cover.png
categories:
  - article
comments: true
tags:
  - hashicorp
  - otto
  - go
  - vagrant
---
- problem: Nomad did not build
- cause: botched fedora Go install
- action: try Otto
- results:
	- build environment created
	- 'make' missing
	- 'make bootstrap' fails: cannot write to /opt/gopath/sources
- fix:
	- add shell script to Vagrantfile that corrects file permissions
- follow up: create PR
- end: rejoice!
