---
layout: post
title: "Otto Dog Food"
author: Bastiaan Bakker
date: 2016-03-10
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
Last Fall Hashicorp launched Otto as the successor to its highly popular Vagrant tool. But is it ready for the spotlight?
Ottos current version, 0.2, lists support for 7 application types. These include Go, the language of choice for Otto itself.
A small dog food test to see whether Otto can build Otto yielded mixed results:
* The *bad*: Ottos Go support does not work out of the box.
* The *good*: but with some small fixes and tweaking Otto provides a workable Go build environment and can build itself.
* The *ugly*: Hashicorp appears to have put Otto on the back burner. The project shows very little activity compared to their other projects.

A case for Otto.
Recently I wanted to write a small feature for Nomad, an excelent scheduler and resource manager for Docker clusters (amongst others).
Like Otto it is written in Go. Unfortunately my Fedora supplied Go environment was botched and failed to build it.
A nice use case to test drive Otto for Go projects.

Otto auto detects Go projects, so a build should consist of a few simple steps, no configuration needed:
1. auto detect the project.
```
cd otto
otto compile
```
2. set up a build environment (in a VM):
```
otto dev
```
3. log in to the build environment
```
otto dev ssh
```
4. perform the build. Here are specific build instructions for Otto
```







```





Hashicorp extensively dogfoods their own tools, so we would expect Otto to be able build Otto itself.
This appears not to be the case yet,



a nice test would be to let Otto build itself.
Recently I had an excuse to try it out for a small use case, essentially the Dog Food test.   






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
