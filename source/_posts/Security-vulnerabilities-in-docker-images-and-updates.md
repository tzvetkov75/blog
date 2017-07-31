layout: post
title: Security vulnerabilities in docker images and updates
date: 2017-04-03 21:12:51
comments: false
tags: 
- docker
- cve
- training
categories: 
- SecTraining 
photos: 
- /images/sec/cve_OS.png
---
	
Docker images are attractive technology for application centristic development. Still, images have security vulnerabilities that requires updates and even building from scratch in some cases. Using images does not remove the need for security updates on libraries.

<!-- more --> 

## Security updates for images
 
Docker images are additional layer bringing agility in the development. As every software, it requires security updates. The reasons can be summarized as:
- Base images, like ubuntu, busybox, centos etc, needs to be updates daily as every modern os. Critical updates can not wait a week to get to production
- Company applications are build over base images and can also need security updates.

Security updates for libs, like libgcc, kernel etc, require to update the image. The options are:
- add the needed lib/files on separate top layer
- load base binary image if available and add your application on the top.
- build your image with application from scratch 

In all cases, you need to build and verify if the application works.

The strategy depends on the company know-how competence and security risk appetite. For example: know-how to build images and potential impact of security.

## Docker are secure due to the sandbox. Why we need to rebuild the image? 

The namespaces and cgroup in linux kernel build sandbox, so inside the container is not possible to access the host. Still, the security is lower than physical machine, see [Docker CVEs](https://www.cvedetails.com/vulnerability-list/vendor_id-13534/Docker.html). Let us not be paranoid, it is good for most of the cases.

The critical security risk is if __an attacker has assess to container__ like: change content of web site, sniff login credentials, use DB connections etc. The main threat is not breaking out of the sandbox (container) than gain access to application in the container.   

## Evaluation of images in DockerHub 

DockerHub has added an excellent feature for scanning the uploaded images against the known CVEs [DockerDocs](https://docs.docker.com/docker-cloud/builds/image-scan/). Additionally, there is nice standalone tool and results see [Block Sec images 2015](https://www.banyanops.com/blog/analyzing-docker-hub/) 

The list is not representative, but snapshot taken on 01.04.2017. We tried to have always two images of certain kind, latest and second best or popular. The purpose of this list is show of the problems that are in the binary images.

### Are this production relevant problems?

This depends strongly on your use case. For example: if there is vulnerability in XML parsing library, but you do not use XML features at all – it is not relevant for you.

Technical application and security responsible must evaluate the threat vector, is this problem applicable for the concrete application. Generally, security professional tend to consider every critical CVE as must be fixed. (risk averse strategy).

From my general experience: less that half of the listed CVEs will have direct impact on your concrete application. Note: this is more enough to start worry

## Results 

The results are generate with script using Docker hub API and provided CVEs scans.

[![CVEs in popular docker images](/images/sec/cve_docker.png)](/images/sec/arch_2.jpg)

## Why there are so many CVEs
 
Probably the main reason is the __chain of dependencies__, aka the the application depends on libs, kernel, base os libs etc. If one of this software components is updated, than all depending components need to be rebuild. 

Furthermore, many fixes are applied __first to master branch__ and later probably ported back to the sable or older branches (versions). Security patch in not applied on all releases in same time and this may cause upgrade of all depending libs to newest version. 



