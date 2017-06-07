---
title: Machine Learning in Security - the Big Picture 
date: 2017-06-06 13:35:09
tags:
 - ai
categories: 
 - AI Firewall
photos:
 - /images/ai/deep_neural_network.jpg
---
There are many scattered information on ML and security. This article provides the starting point for beginners.
<!-- more --> 
## Why is is so difficult?

ML and security is around over 20 years: starting with Intrusion Detection Systems around 1984-86 at [SANS](http://www.sans.org/reading-room/whitepapers/detection/history-evolution-intrusion-detection-344) . Still, there are many white spots and we are on the beginning. The main challenges can be summarized in next chapters

### Lack of labeled data ###
The label data is generated manually by selecting training sets (right and wrong). It is quite difficult to create ML usable volume of data representative for security.
### Anomaly detection dimensions ### 
Anomaly detection is good choice, if there is not reliable labeled data. The NOC (Network Operation Center) is very typical place to look at. 
[![Sysdamin Stats](/images/ai/stats_small.png)](/images/ai/stats_small.png)

The security threats typically are so multidimensional and  can not presented them on simplified CPU usage stats. Security attack may take days with very low activity. 
### Patterns changes: updates, changes and new services ###
Every update of technical framework, patches, new services may cause change in patterns and leads to false-positive. Basically the ML must be trained to some degree again. This is huge operational overhead. 
### Lack of data to the open community ###
Where to get real data, aka real logs? This is big problem. Most of the companies will never disclosed logs to the community.
Anonymisation can not solve the problem fully since it wipes valuable part of the information, like distribution etc. True anonymization is far more then wiping credit card numbers.
#### Honeypots
Honeypots are really useful, but provide only attacker logs. ML needs mix of good and bad connections.
### Limited time ###
The decision if an attack has happened and how to respond, must be taken in seconds. We can not wait 2 weeks to simulate, train ML, discuss etc. Even with human support it is difficult to pro-actively react.(postfactum is definetely easier)

### IP address limitations ###
Many services report based on IP, but serious attack will rotate the IP addresses - one time usage per significant attack. This is extremely simple and effective around all reputation servicves.

### Constantly evolving attacks ###
The attacks permanently change not only between layers, but scope and objects targets.

### Limited understanding ###
The IT  world of typical Sys Admin (SRE) is sure vary complex, but with different complexity than in Machine Learning problems. There is little understanding of the problem in sys operations and R for sys admin problems.

### Solutions and Related projects

Solutions are very particular to certain problems, like fishing mails. Probably we will not have big ML Security brain for everything. 
Key point on effective solution is national or EU wise __nonprofit and open  cyber security center__ that will collect logs/data from companies (infrastructure, tel cos etc) and will provide mandatory protections system. The EU is going in this direction. Still, there are many problems to solve: efficient political control model, reliable technical solution and administrative organization. No one wants bureaucracy that a real protection of the companies. 

Small companies, supported by EU programs, can develop needed know how and provide solid basis for national cyber center. 

What is our solution? Wait and you will see ;-)

## List of interesting projects:

- [MLSec Project](https://www.mlsecproject.org/) very nice talk on general problems of ML in security. 
- [ML and security](http://fsecurify.com/machine-learning-and-cyber-security/) links list with ML in security
- [Threat Intelligence resources](https://github.com/hslatman/awesome-threat-intelligence). Very nice list of Threat sources
- [Sec Repo](http://www.secrepo.com/) Contains publicly available datasets that are great value
- [Public PCAP](http://www.netresec.com/?page=PcapFiles) public available pcap files
- [Modern Honey Network](https://threatstream.github.io/mhn/) if you want to get you data form honeypot
- [Honeypot project](https://www.honeynet.org/about) with valuable infos
- [Machine Learning for Cyber Security](https://github.com/wtsxDev/Machine-Learning-for-Cyber-Security) List of resources
- [List recourses ML and security](http://www.covert.io/) seems very promissing

Companies (I have no relation to them :-):  

- [Zenedge AI FW](https://www.zenedge.com/ai-waf)
- Free [SIEM](https://siemonster.com/)


---
