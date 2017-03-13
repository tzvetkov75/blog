---
title: Challenges for Machine Learning in Security
date: 2017-03-13 22:30:37
tags:
 - ai
categories: 
 - AI Firewall
photos:
 - /images/ai/brain.jpg
---
Security and Machine Learning is essential for next generation of security protection systems. Complexity of the threads, big data, speed of development, importance of security leads to next big phase in the security integration with big data and machine learning.

<!-- more --> 
## Introduction

Machine Learning(ML) is the consequence of the big data. We have the the big data now, so how can we understand it. ML trend is not new and it is already well integrated inimage recognition, web page ranking, stock prediction etc. 

### Why is ML so critical for the IT Security? 

Probably, because the next violent war will be carried also over Internet.

Internet is noisy place,  many events that is is difficult to see what is critical and what is not. Even an event with less echo at the moment can result in devastating leak in several weeks.

Semi manually, by reading logs and generating rules, is not the right approach in big data. Signatures, like by AntiVirus software is never going to work. 

## Dirty secrets form Security Operation Centers (SOC)

[![Security Operation Center](/images/ai/soc.jpg)](/images/ai/soc.jpg)

On every IT Security Officer peresentation, there is the __dream of Network and Security Operation Center__. Security Analysts evaluating the alarms and either escalates or marks as false-positive. This is idyll and in many cases not real.

The back side of the medal:  Security Analyst sees some logs marked as alarms: 
- Is this normal caused by some update of some application that we have over thousand? Even a patch of system can lead to suspicious network activity.
- The Analyst does not know all application, probably last version of office 365 cloud work like this. What can security Analyst do:
- Browse the web and ask colleagues – this is not prevention - too slow the attack was probably finished.
- Call the Product Owner and ask if every think ok (have you been hacked). The owner and hist colleagues are many cases to really the right one.
- Try to pass the problem to someone else, like cover you ass principle
- Mark it as false alarm and hope the company is not hacked.
- In very rare cases and young and motivated professional, can stop to connection. He wants to understand. After explaining to his boss and business owner why the service is not available, he will never be the same. This is the difference between newbie and the experiences.

The sentence is:
>SOC can handle excellently easy problems, like access from the wrong IP. Complex technical threads can not be handled in this way because of lack of deep know how.

The attack analysis can be very complex and time intensive. Attack itselv is many time easyer to generate.

### Hecker is not best security developer

Please notice
>It is easier to break a system that to build one.

In other words, because a hacker knows how to break the system, does not automatically qualify him for best to build the security system. Both collegues need to learn from each other with respect.

Security Analyst must be __creative__ hacker by __know how__, but with high level of __discipline__. IT is rare to find creative with good discipline - call it exception. This is polar qualities. We need to combine them and not to look for ideal profile.

## Challenges and Difficulties with ML and security 

The biggest challenge is the detection of anomalies or expressed in research term – generating the labeled data. You need to train the system in the way that is can recognize normal behavior. 

Security system need permanent __feedback if the system is not hacked__ or even how deep potential attack is suceeding.

This is very complex task, since:

- __Postfactum__ - Many devastating hacks, like on Yahoo, were detected only after publishing the info in dark net. This is too late for security as everyone may gues.
- __Know How__ Even application developer does not understand their applications fully, because of the complexity
- __Frameworks__ lead that application developer are not aware of serialization types, network protocols and some low level behavior.

