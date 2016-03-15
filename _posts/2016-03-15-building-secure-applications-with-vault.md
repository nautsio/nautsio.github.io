---
layout: post
title: "Building secure applications with Vault"
author: Erik Veld
date: 2016-03-15 10:00
cover: /img/2016-03-15-building-secure-applications-with-vault/cover.jpg
preview: /img/2016-03-15-building-secure-applications-with-vault/cover.jpg
categories:
  - article
comments: true
tags:
  - vault
  - hashicorp
  - security
  - event
  - training
  - xebia
---
Storing and granting access to sensitive information and secrets is a difficult problem to solve, and it's easy to accidentally introduce security issues along the way. Every organization has to store secrets or other sensitive information and have it be accessible to individuals or systems. These secrets can be database credentials, cloud provider credentials, API keys, etc.

How do you share them without them being open to attack? And if something does occur, how can you see what information was requested by whom and revoke the affected keys. One of the products that tries to provide answers to these question is HashiCorp's [Vault](https://www.vaultproject.io/).

Vault secures, stores, and tightly controls access to tokens, passwords, certificates, API keys, and other secrets in modern computing. Vault handles leasing, key revocation, key rolling, and auditing.

![Vault](/img/2016-03-15-building-secure-applications-with-vault/vault.png)

> Secure your applications and infrastructure to limit the surface area and attack time in the event of a breach.

What better way to learn how to manage your secrets and how to build secure applications with Vault than from the source? On the 31st of March HashiCorp's [Seth Vargo](https://twitter.com/sethvargo) will be giving an [engineer-led course](https://ti.to/hashicorp/training-amsterdam-building-secure-applications-with-vault) in Amsterdam, aimed at both Vault administrators operationalizing vault and developers writing applications that utilize Vault secrets.

<script type="text/javascript" src="http://maps.google.com/maps/api/js?sensor=false"></script>
<div style="overflow:hidden;height:500px;width:960px;"><div id="gmap_canvas" style="height:500px;width:960px;">
  <a class="google-map-code" href="http://www.map-embed.com" id="get-map-data">NH Collection Grand Hotel Krasnapolsky</a>
  <style>#gmap_canvas img{max-width:none!important;background:none!important}</style>
</div>
<script type="text/javascript"> function init_map(){
  var myOptions = {
    zoom:15,
    center:new google.maps.LatLng(52.37258780000001,4.894780200000014),
    mapTypeId: google.maps.MapTypeId.ROADMAP,
    scrollwheel: false
  };map = new google.maps.Map(document.getElementById("gmap_canvas"), myOptions);marker = new google.maps.Marker({map: map,position: new google.maps.LatLng(52.37258780000001, 4.894780200000014)});infowindow = new google.maps.InfoWindow({content:"NH Collection Grand Hotel Krasnapolsky" });google.maps.event.addListener(marker, "click", function(){infowindow.open(map,marker);});}google.maps.event.addDomListener(window, 'load', init_map);
</script>
</div>

The first part of the course covers the **operational components** of Vault including:

- Initializing a Vault
- Understanding secrets and leases
- Mounting and configuring secret backends with Vault
- Configuring and parsing audit backends with Vault
- Deploying Vault in an HA environment

The second part of the course covers techniques for **integrating Vault secrets into applications** including:

- Using [Consul Template](https://github.com/hashicorp/consul-template) and [Envconsul](https://github.com/hashicorp/envconsul)
- Communicating directly with Vault in your application

After this training you will be able to set up Vault, store your secrets and sensitive information, and create applications that make use of Vault to store its secrets.
