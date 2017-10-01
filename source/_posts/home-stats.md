layout: post
title: Collect statistics for Internet usage in small/home networks
date: 2017-09-24 21:29:59
tags:
 - statistic
 - home network
 - security
categories: 
 - blog
photos:
 - /images/blog/domain_dump.jpg
---
Getting some Internet content statistics from small network can be challenging task if limited resources are available. Here I propose extractiong TLS SNI extension and HTTP host header approach, where you do not introduce single point of failure, like DNS resolver or Web Proxies.
<!-- more --> 

## Before you begin 
There can be many reason why you need to know what are the accessed domains from the nodes:
- smart devices, like TV, set top boxes, access frequent very “strange” sites
- IoT devices, like smart lights, coffee machines etc. There are black boxes for the users.
- software on computers  from semi trusted vendors
- users browsing behavior
> You need to ask for consent of network users, since spying private communication is amoral and can be illegal in your country.
 
## How can be done
There are multiple ways how can be done;
- __DNS resolver log__ The advantage is this is very easy to achieve: every host needs to resolve the domain before accessing it. You can assign own reslover with extended los. Drawback is that resolving is cached at host and it is not sure how frequent the domain is accessed(DNS TTL). It can be 24h after resolution. Second disadvantage is that is can be single point if failures if the resolver fails.
- __Extraction of TLS SNI and Host header__ You can mirror the port(s) on switch and extract on the fly TLS SNI extension and Host header. Advantage: it is not single point of failure (you loose only stats if the script stops) Disadvantage: you need a node to dump the traffic and mirror ports on switch. Alternatively you can run dump script on router. Furthermore, you can not see following request in the same domain at the same TLS session.
- __Proxy__ (web washer) that interrupts the TLS session. This will give you most statistics – even exact URLs. The big disadvantage is its maintainance complexity. Proxy is bottle neck of internet access speed. Furthermore, it is again single point of failure and not all software support proxies. You need to know how you configure all IoT software for this.  

## Extracting SNI extension and Host header 

Here I describe the second option, thus extracting the [SNI extension](https://en.wikipedia.org/wiki/Server_Name_Indication) from TLS handshake (ClientHello) and Host header from HTTP request. It not so popular as DNS but I found it very interesting. 

You will need TCDPDUMP, TSHARK and BASH and AWK to used it. These are available  on all unix os. The script is extremity simple and you can find it on following link 

[Domain Grep](https://github.com/tzvetkov75/domain_grep) 

^ You will find there how to use it too.

### Network diagram

The best is if you have spare small unix device, like Raspberry-Pi that you can connect on mirroring port in you network.

[![Network diagram](/images/blog/mirror.png)](/images/blog/mirror.png)


The usage output 

```
# ./domain_grep.sh eth0
listening on interface eth0

tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 1500 bytes
Sep 29, 2017 13:46:05.756451000 CEST    Domain_grep     192.168.1.36    https://www.wired.com
Sep 29, 2017 13:46:05.766029000 CEST    Domain_grep     192.168.1.36    https://acs.lavasoft.com
Sep 29, 2017 13:46:05.904757000 CEST    Domain_grep     192.168.1.36    https://assets.adobedtm.com
Sep 29, 2017 13:46:05.906292000 CEST    Domain_grep     192.168.1.36    https://media.wired.com
Sep 29, 2017 13:46:05.906807000 CEST    Domain_grep     192.168.1.36    https://media.wired.com
```

## Visualization

You can use ELK (Kibana, Logstash, Elasticsearch), Splunk or any of your favorite tools to visualize it. 
