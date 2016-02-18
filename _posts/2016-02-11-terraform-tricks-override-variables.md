---
layout: post
title: "Terraform tricks: Override variables"
author: Benny Cornelissen
cover: /img/2016-02-11-terraform-tricks-override-variables/terraform-cover.png
categories:
  - article
tags:
  - terraform
  - hashicorp
externalurl: http://blog.bennycornelissen.nl/terraform-tricks-override-variables/
---
I have been using Terraform in production for almost a year and the experience has been pretty great so far. However, Terraform does have some shortcomings. In the Terraform Tricks blog series I want to show how to work around some of these shortcomings, as well as explore some of the less-known (or undocumented) awesomeness of Terraform. In this blog post I will discuss various options for overriding variables without the need for excessive code-duplication.
