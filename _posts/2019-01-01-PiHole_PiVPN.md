---
layout: single
title:  "Pi Hole and Pi VPN on Raspberry Pi"
date:   2019-01-01 15:03:38 -0400
author: JS
categories: web
tags:
  - Raspberry Pi 
  - VPN
  - DNS
header:
  teaser: /assets/images/PiHole.jpg
excerpt: Host DNS/VPN on Raspebrry Pi.
---

My little Raspberry Pi has been sitting at the corner for a while now with all the dust. Until recently, PiHole showed up in one of my friends' blog. It is a lightweighted DNS server with the a nice Web interface to easily block certain DNSs (mostly for ads). Another idea I wanted to test out is to set up my own VPN, for security purpose.

I declare no expertise in internet stuff like DNS or VPN. Below are some notes collected so far, and they work!

## Pi Hole
It sounds fun and it is fairly easy to setup. I will cut the steps here, as there are a quite a few very good instructions (e.g., [this one](https://mall.10046.mi.com/fanscard/index)). After setup, you will have this nice dashboard to monitor all the activities.
![PiHole](/assets/images/PiHole.jpg)

## Pi VPN
VPN is another thing I wanted to setup. My router is a bit old, which only supports PPTP. That's said to be less secure nowadays. [PIVPN](http://www.pivpn.io/) is a customized (or say optimized) OpenVPN. Again, many helpful instructions (e.g. [this one](https://www.smarthomeblog.net/raspberry-pi-vpn/)) are available. 

## Combining the Two
The next step is to let all VPN connection go through our new DNS server (PiHole). For this one, the shared information on-line varies quite a lot. [This one](https://forum.xda-developers.com/showpost.php?p=76023719&postcount=5) works for me, at least. 

With all this, the combination of OpenVPN + PiHole should work now. To test if it works, you should be able see your log under "Query Log". The connection from OpenVPN is often from its own subnet like 10.8.0.*.

## Publish IP 
One bonus point is how to know what IP address to connect to, as most of our IPs are not static. I used to have a simple script which sends an email to myself whenever the IP changes. This time, I find a free dynamic DNS host provider [DuckDNS](https://www.duckdns.org/). All you need to do is to register your IP with a subdomain like ''XXX.duckdns.org''. On your Pi, add a recurring schedule (e.g., using cron) to update your IP to DuckDNS every few minutes. Now you can use ''XXX.duckdns.org'' for VPN connection. 

## Lastly
One potential drawback of using Raspberry Pi is its network speed. With an USB wifi dongle, I am able to achieve ~10Mbits/Sec. But it is still enough for watching Youtube or surfing on internet. I might consider an upgrade once both Pi's network adapter and I/O got upgraded. So far, I can live with that.



