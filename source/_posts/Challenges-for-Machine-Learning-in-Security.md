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
Security and Machine Learning is essential for next generation of protection systems. Complexity of the threads, big data, speed of development and criticality of security lead to next major phase - integration of security with machine learning and big data.

<!-- more --> 
## Introduction

Machine Learning(ML) is the consequence of the big data. We have the the big data now, so how can we understand it from security prespective. ML trend is not new. ML is already well integrated in image recognition, web page ranking, communication protocols, stock prediction etc. Still for the security is still not well integrated.

### Why is ML so critical for the IT Security? 

Probably, because the next violent war will be carried also over Internet.

Internet is noisy place, many events and it is difficult to differentiate what is critical and what is not. Even an event with less echo at the moment can result in devastating leak in several weeks.

Semi manually,aka reading logs and generating rules, is not the right approach in big data. Signatures, like by AntiVirus software is never going to work. 

## Dirty secrets form Security Operation Centers (SOC)

[![Security Operation Center](/images/ai/soc.jpg)](/images/ai/soc.jpg)

On every IT Security Officer presentation, there is the __dream of Network and Security Operation Center__. Security Analysts evaluating the alarms and either escalates or marks as false-positive. This is idyll and in many cases not real.

The back side of the medal:  Security Analyst sees pre classified logs marked as potential attacks.
- Is this normal caused by some update of some application. SOC supervise over thousand. Even a patch of system can lead to suspicious activity.
- The Analyst does not know all applications, aka probably last version of office 365 works like this. 

What can security Analyst do:
- Browse the web, compare between environments and ask colleagues – this is not prevention - too slow the attack was probably finished.
- Call the Product Owner and ask if everything is ok, aka have you been hacked?. The owner and his colleagues are in many cases to really the right ones.
- Try to pass the problem to someone else -  cover you ass principle
- Mark it as false alarm and hope the company is not hacked this time
- In very rare cases, a young and motivated professional, can block the application. He wants legitimately to understand first. After explaining to his boss and business owner why the service is not available, he will never be the same. This is the difference between newbie and the experiences.

The sentence is:
>SOC can handle excellently easy problems, like access from the wrong IP. Complex technical threads can not be handled in this way because of lack of deep know how on certain application.

The attack analysis can be very complex and time intensive. Attack itself is many time easier to generate.

Very little SOC are in position to block sophisticated attacks realtime.

### Hacker is not best security developer

Please notice
>It is easier to break a system that to build one.

In other words, because a hacker knows how to break in the system, does not automatically qualify him for best to build the security system. Both colleagues developer and ethical hacker need to learn from each other with respect.

Security Analyst must be __creative__ hacker by __know how__, but with high level of __discipline__, lookin in alarm for hours. Both in one person is rare to find - call it exception. These are semi polar qualities. We need to combine them and not to look for ideal profile, like in many cases.

## Challenges and Difficulties with ML and security 

The biggest challenge is the detection of anomalies or expressed in researcher words: generating the labeled data. You need to train the system in the way that is can recognize unknown attacks – 0 day exploids. 

Security system need permanent __feedback if the system is not hacked__ or better how deep potential attack is succeeding.

This is very complex task, since:

- __Post factum__ - Many devastating hacks, like on Yahoo, were detected only after publishing the info in dark net. This is too late for security as everyone may guess.
- __Know How__ Even application developer does not understand their applications fully, because of the complexity. 
- __Frameworks__ lead that application developer are not aware of serialization types, network protocols and some low level behavior.

