---
layout: post
title: Scheduling containers and more with Nomad
author: Erik Veld
date: 2016-02-03
---
Specifically for the <a href="#">Dutch Docker Day</a> on the 20th of November, <a href="#">HashiCorp</a> released version 0.2.0 of <a href="#">Nomad</a> which has some awesome features such as service discovery by integrating with Consul, the system scheduler and restart policies.  HashiCorp worked hard to release version 0.2.0 on 18th of November and we pushed ourselves to release a self-paced, hands-on workshop. If you would like to explore and play with these latest features of Nomad, go check out the workshop over at <a href="#">http://workshops.nauts.io</a>.

Last friday, November the 20th, was the first edition of the Dutch Docker Day where I helped prepare a workshop about "scheduling containers and more with Nomad". It was a great experience where attendees got to play with the new features included in 0.2.0, which nearly didn't make it into the workshop.

When HashiCorp released Nomad during their <a href="#">HashiConf</a> event at the end of September, I was really excited as they always produce high quality tools with great user experience. As soon as the binary was available I downloaded it and tried to set up a cluster to see how it compared to some of it's competitors. The first release already had a lot of potential but also a lot of problems. For instance: when a container failed, Nomad would report it dead, but take no action; restart policies were still but a dream.

<div><img src="https://iroller.io/content/images/2015/09/IMG_2373.JPG" /></div>

There were a lot of awesome features in store for the future of Nomad: integration with <a href="#">Consul</a>, system jobs, batch jobs, restart policies, etc. Imagine all possible integrations with other HashiCorp tools! I was sold. So when I was asked to prepare a workshop for the Dutch Docker Day I jumped at the opportunity to get better acquainted with Nomad. The idea was that the attendees of the workshop, since it was a pretty new product and had some quirks, would go on an explorative journey into the far reaches of the scheduler and together find it's treasures and dark secrets.

> We were told that there would be a new version released before the Dutch Docker Day but nothing appeared, until the day before the event.

Time went by and the workshop was taking shape nicely. We have a nice setup with a cluster of machines that automatically bootstrap the Nomad cluster and set up it's basic configuration. We were told that there would be a new version released before the Dutch Docker Day but nothing appeared, until the day before the event. I was both excited and terrified! The HashiCorp team worked long hours to get the new release of Nomad done in time for the Dutch Docker Day so <a href="#">Armon Dadgar</a>, the CTO of HashiCorp and original creator of Nomad, could present the new features during his talk. This of course is a great thing, except for the fact that the workshop was entirely aimed at 0.1.2 and we had none of these new features incorporated into our Vagrant box. Were we going to throw all our work overboard and just start over, the night before the event?

It took until late in the evening to get an updated <a href="#">Vagrant box</a> with a bootstrapped Consul cluster and the new Nomad version, in order to showcase the auto discovery feature and Consul integration that 0.2.0 added. However, the slides for the workshop were still referencing the problems we encountered when trying out the 0.1.0 and 0.1.2 release, so all the slides and statements we had made about things not working or being released in the future had to be aligned with the fixes and improvements that came with the new release. After some hours of hectic editing during the morning of the event, the slides were finally updated and showcased all the glorious new features!

<div><img src="https://iroller.io/content/images/2015/09/IMG_2374.JPG" /></div>

The new features they added in this release and the amount of fixes and improvements is staggering. In order to discover services there is no longer a need for extra tools such as Registrator, and your services are now automatically registered and deregistered as soon as they are started and stopped (which I first thought was a bug, cause I wasn't used to Nomad actually restarting my dead containers). The system scheduler is another feature I've been missing in other schedulers for a while, as it makes it possible to easily schedule services (such as Consul or Sysdig) on all of the eligible nodes in the cluster.

If you would like to follow the self-paced workshop by yourself, you can find the slides, machines and scripts for the workshop at <a href="#">http://workshops.nauts.io</a> together with the other workshops of the event. Please let me know your experiences, so the workshop can be improved over time!

{% prism go %}
//
// Get details about a group in Active Directory.
//
func getGroup(c *cli.Context) {
if len(c.Args()) < 1 {
cli.ShowSubcommandHelp(c)
os.Exit(1)
}

groupID := c.Args()[0]
credentials := readCredentials()

address := fmt.Sprintf("https://graph.windows.net/%s/groups/%s?api-version=1.6",
credentials.Company, groupID)
client := &http.Client{}
req, err := http.NewRequest("GET", address, nil)
req.Header.Add("Host", "graph.windows.net")
req.Header.Add("Authorization", credentials.Token.AccessToken)
req.Header.Add("Content-Type", "application/json")
req.Close = true

resp, err := client.Do(req)
check(err)

content, err := ioutil.ReadAll(resp.Body)
check(err)

fmt.Println(string(content))
}
{% endprism %}

I would like to thank the HashiCorp team for their amazing work on the 0.2.0 release, the speed at which they have added so many great new features and improved the stability is incredible.

It was a lot of fun preparing the workshop for the Dutch Docker Day. Working with bleeding edge technologies is always a great way to really get to know it's inner workings and quirks, and I would recommend it to anyone, just be prepared to do some last-minute work ; )
