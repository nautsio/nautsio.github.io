---
author: Sebastiaan van Steenis
tags: docker
difficulty: basic
externalurl: http://blog.xebia.com/security-is-maturing-in-the-docker-ecosystem/
---
Security is probably one of the biggest subjects when it comes to containers. Developers love containers, some ops do as well. But it most of the time boils down to the security aspects of containers. Is it safe to use, what if someone breaks out? The characteristics of containers which we love, could also be a weak spot when it comes to security. In this blog I want to show some common methods to establish a defence in depth around your containers. This is container-specific, so I won't be talking about locking down the host nodes or reducing the attack surface i.e. by disabling Linux daemons.
