---
title: Honey pots with docker  
date: 2017-06-02 23:01:25
tags:
 - honeypot
 - security
categories: 
 - blog
photos:
 - /images/blog/honeypot.jpg
---
Honey pots are very import for the security and very underestimated in the enterprises. They are very important sensors for attacks and make is significantly difficult for attackers. Docker brings isolation of the honey pots that is vital, since hacked honey pot can contaminate all networks.
<!-- more --> 

## Importance of honey pots

Assume the attacker scans 20 online host in the network but 10 are honey pots. There is 50% of chance to be sensored and isolated if the honey pots are internal mock up. 

## Intranet is important

Major part of the attacks are coming from insider, so intranet must also have honey post. Important for this is to be keeped as secret as possible.

Poorly set honey pot can lead to compromise of the hole network. 

They can be used as jump host to management, backup networks in hop by hop manner. It is important to isolate honey pot and not blindly trust all data coming from, like:
- arp, dns, ip etc. 
- logs, snmp other events
- coping files from, like config, backups etc


[![KRITIS	](/images/blog/KritisKreis.png)](/images/blog/KritisKreis.png)


---
