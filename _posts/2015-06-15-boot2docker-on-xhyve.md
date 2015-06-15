---
externalurl: http://simonvanderveldt.nl/boot2docker-on-xhyve/
author: Simon van der Veldt
category: blog
title: "boot2docker on xhyve"
---
xhyve is a new hypervisor in the vein of KVM on Linux and bhyve on BSD. It’s actually a port of BSD’s bhyve to OS X.
It’s more similar to KVM than to Virtualbox in that it’s minimal and commandline only which makes it a good fit for an always running virtual machine like boot2docker on OS X.
This post documents the steps to get boot2docker running within xhyve and contains some quick benchmarks as well to compare xhyve’s performance with Virtualbox.
