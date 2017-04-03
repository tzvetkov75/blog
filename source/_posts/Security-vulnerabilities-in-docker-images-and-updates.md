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

Docker images are attractive technology for application centrist development. Still, images have security vulnerabilities that requires updates and even building from scratch. Using images does not remove the need for security updates on libraries.

<!-- more --> 

## Security updates for images
 
Docker images are additional layer bringing agility in the development. As every software it requires security updates. The reasons can be summarized as:
- Base images, like ubuntu, busybox, centos etc, needs to be updates daily as every modern os. Critical updates can not wait a week to get to production
- Company applications are build over base images and can also need security updates.

Every time security update is published for lib, like libgcc, we need to update and __build the image__

In worst case, the image must be build from scratch - no binary build image at DockerHub at the moment. 

For example if Jboss/wildfly is build every day, but the image is published to dockerHub every two days. Risk Management must decide what to do in the case of critical update.

## Docker are secure due to sandbox. Why we need to update docker? 

The namespaces and cgroup in linux kernel will build sandbox, so container will not able to access the host in most of the cases. Still, the security is lower then physical machine, see [Docker CVEs](https://www.cvedetails.com/vulnerability-list/vendor_id-13534/Docker.html) . Let us not be paranoid, it is good for most of the cases.

If an attacker has __assess to container is critical__ in most of the cases:  change content of web site, read login credentials, use DB connections etc. The main threat is not breaking out of the sandbox (container) than gain access to the container application is enough.   

## Evaluation on DockerHub 

DockerHub has started an excellent feature for scanning the uploaded images against the known CVEs [DockerDocs](https://docs.docker.com/docker-cloud/builds/image-scan/). Additionally there is nice standalone tool and result s [Block Sec images 2015](https://www.banyanops.com/blog/analyzing-docker-hub/) 

Here you can see the summary list of most used images. 

The list is not representative snapshot taken on 01.04.2017. We tried to have always two images of certain kind, latest and second best or popular. The purpose of this list is show of the problems that are in the images.

### Are this production relevant problems?

This depends strongly on your use case. For example: if there is vulnerability in XML parsing library and you do not use XML at all – it is not relevant for you.

Technical application and security responsible  must together evaluate the threat vector, thus is this problem applicable for the concrete application. Generally, security professional tend to consider every critical CVE as must be fixed. (risk averse strategy).

From my general experience: less that half of the listed CVEs will have direct impact on your concrete application. Note: this is more enough to start worry

## Result 

The results are generate with script using Docker hub API and provided CVEs scans.

[![CVEs in popular docker images](/images/sec/cve_docker.png)](/images/sec/arch_2.jpg)




