---
author: Richard Woudenberg
tags: docker
cover: /img/2015-03-18-reducing-your-docker-image-size/container-cover.png
difficulty: basic
externalurl: http://woudenberg.io/reducing-docker-image-size/
---
Using the basic [Dockerfile syntax](https://docs.docker.com/reference/builder/) it is quite easy to create a fully functional Docker image. But if you just start adding commands to the Dockerfile the resulting image will become bigger and bigger.
A few basic actions can reduce your image size significantly.
