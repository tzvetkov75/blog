﻿---
title: Lightweight Security Framework for Software Developer
date: 2017-03-08 22:55:33
comments: false
tags: 
- secarch
- training
categories: 
- SecTraining 
photos: 
- /images/sec/arch_3.jpg
---
Common Security Frameworks, like ISO 27 000, x805, BSI 100 etc, are too abstract and far away from most software developer. We set focus on the developer, so he can understand security. 

Existing security frameworks are all  excellent comprehensive models from security point of view,  like: ISO 27000, COBIT, BSIMM-V, BSI 100, x805, NIST SP 800-12, Basel II, Cisco SCF etc. 

Drawback of the security models is the huge information and missing integration in the various developing models. The development use agile, scrum, waterfall, ITIL etc. style of development and it is not obvious how it maps to the security model.  

<!-- more --> 
The trend: agile and rapid development does not fit in the heavy security models. It looks like a dinosaurs of security and mouse of tiny agile development. The security mainly uses top-down approach, multiple committees, segregation of duties etc. The development currently makes shots cycles, sprints of 14 days for example, continuous development, flat hierarchies etc. It is very difficult to handle agile models with heavy security standards.

All this motivated me to develop as light as possible security models which are:

- Understood by the developers and reflect most common development cycle
- Cover as many as possible security aspects and be touch-point to security departments
- Do not require intensive study than a short lookup to get the point 

## Common ITIL Development Phase

According to ITIL there are three main phases relevant for the security: 
- Design
- Transition
- Operation. 

Additionally, there are strategy and improvements that I will not put in focus. 
I would add implementation, but this can make the framework significantly complext (next time)


## Model for developer

This model bases on ITIL cycle as most common, but sure can fit in ISO 9000 Plan-Do-check-Act. The is not comprehensive as iso 27 000, buts cover most of the security problems and the main point it is understandable for developer.

__Single Page Model__ ,so no need to read a book for weeks. If you understand this you have covered significant part of the security aspects.

_(click to enlarge)_
[![Lightweight Security Framework](/images/sec/arch_2.jpg)](/images/sec/arch_2.jpg)
## Design Phase: 

There 7 important security questions which needs to be discussed

- __Authentication__ How to you assure only authorized user access features (data). 
 - Horizontal attack - user A tries to access information on other user B 
 - Vertical attacks: User A try to obtain higher administrator rights
- __Integrity__ can you audit the data or is it needed to be audited by the legal authorities?
- __Intrusion__ What are you protecting from? Thus: insider, internet user, intranet, hardware access etc. This must be very clear before designing any technical mechanisms. 
- __Risk management__. You may want to protect from all possible attacks, but costs will not allow this for sure.  Risk management (risk = potential loses X likelihood)  helps you at early stage to agree what are the risks to be address : you may implement some countermeasures to reduce the risks (mitigation). Alternatively, you may transfer the risk to some else (who is better paid and you hate).  Risk Acceptance means it is not worth of inversing in mitigation. With Risk Reject you agree that this cannot be handled and stop the service.
- __Security Architecture__ This is the main part, where the technical aspect are described (similar to high and low level design)  
- __Tool, Libs, Frameworks__ - define the stack from security point of view   
- __Solution design__ - define low level, system design 
- __Implementation__ - exact implementation, aka code, parms etc. This can be also set as different phase, but to be consistent to ITIL we set it as part of the development.

It is very important to understand that you have two aspects

- __Service__ for Example an  E-Banking Service 
- __Infrastructure__ (OS, Application Server, Network) 

There are different planes, which need to be covered:

- User Plane, where you deliver the service
- Provisioning, where you automatically provision customer (probably) by the business, back office process etc.
- Management and Administration   as part of the general Service training 
- __Simulation__.  You should practice some precedents to see how the organization and processes are working.  The exercise are extremely important, think on fire exercises.

## Operation

- __Security Monitoring__ you cannot improve without quantitative measurement. The main problem is  conflict of interests regular independent audit.
- __Performance and Availability__

## The Big Picture 


[![Big Picture](/images/sec/arch_3.jpg)](/images/sec/arch_3.jpg)

There is another small drawing which explains the relation between: 
- __Security strategy__ (long term) - signed by CxO
- __Policy__ (medium terms) - signed by IT Officer, CTO and other strike-holder
- __Security technical standard__ Explains how technical patterns should look with concentrate security settings
- __Best Praxis__ This is group of well known and recognized standards, like OWASP.

To realize security there must be three pillars: 
- __Organization__ - roles and structures for doing security
- __Resources__  technical tools,  people
- __Process__ there must be clear processes 

The security development cycled is part of the product development cycle.

[![Phases](/images/sec/arch_1.jpg)](/images/sec/arch_1.jpg)
