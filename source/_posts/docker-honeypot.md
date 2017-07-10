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
Honey pots are very import for the security and underestimated in the enterprises. They are very important sensors for attacks and make is significantly difficult for attackers. Docker brings isolation of the honey pots that is vital, since hacked honey pot can contaminate all networks.
<!-- more --> 

## Importance of honey pots

Assume a hacker scans and attacks 20 online host in the network, but 10 of them are honey pots. There is 50% of chance to be sensored in simplified scenario. The more a honey pot is close to real server, the bigger the chance to attract an attacker.

## Intranet is important

Major part of the attacks are coming from insider, so intranet must also have honey post. Important for this is to be keept as secret as possible.

## Poorly isolated honey pots lead to compromise of the hole network. 

They can be used as jump host to management, backup networks in hop by hop manner. It is important to isolate honey pot and not blindly trust all data coming from, like:
- arp, dns, ip etc. 
- logs, snmp other events
- coping files from, like config, backups etc

## Isolated Docker for honey pot 

Docker can run isolated in network and resources due to name-spaces in Linux. They are perfect match for using honey pots.

## Setting network isolation 

Every docker container is added default to bridged network, assume the following constellation. That is very classical.

[![Network Pots](/images/blog/pots.png)](/images/blog/pots.png)

> you have multiple network spaces, routing tables and ip tables.

Every docker container has its own firewall(iptable), v-interfaces, routing table. What is FORWARD for the global ip table, it is is INBOUND for the other etc.

## Docker network 

Build you own bridged network in docker and attacker all honey pots to it. You do not need NATP (masquerading) in order to make the pots reachable from outside.

``` bash
docker network create --driver=bridge --subnet=172.17.0.0/16 \
      -o "com.docker.network.bridge.enable_ip_masquerade"="false" vess_br0 

```

## IPtable Isolation of container

>The target solution if someone has hacked the container with honey pot and has full root access than he can not establish any connection outside.

We need to add the following rules

- __Forwarding__ DROP New connection from Pot container to local networks 

``` bash
 sudo /sbin/iptables -I FORWARD 1  -d 172.172.0.0/16,192.168.0.0/16 \
     -s 172.172.0.0/16 -m state --state NEW -j DROP 
```

as first rule in the global forwarding table

- __INPUT__ DROP new connection from Pot container to the host 

``` bash
 sudo /sbin/iptables -I INPUT  1  -d 172.172.0.0/16,192.168.0.0/16 \
    -s 172.172.0.0/16 -m state --state NEW -j DROPP 
```
as first rule in the global input table

- __OUTPUT__ DROP (optional) new connections from Host to local network This is optional rule and may not needed in all scenarios 

``` bash
sudo /sbin/iptables -I OUTPUT 1  -d 172.172.0.0/16,192.168.0.0/16 \
     -s 172.172.0.0/16,192.168.0.0/16 -m state --state NEW -j DROP
```

as first rule in the global output table

__DONE__ with network part 

---
