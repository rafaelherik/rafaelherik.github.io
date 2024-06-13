---
layout: post
title:  "Hello Podman"
date:   2024-06-11 19:29:49 +0200
categories: containers
---

# Podman

![Alt text](assets/podman-logo.png){width=300;}


I've been working with containerized applications for a while, mostly docker based, but for a long time **podman** is capturing my attention for a long time. **Podman** stands out from other container engines for one main reason, it's demonless. To give some context, ***WHAT IS DAEMON?*** Daemons are processes that run in background to do the heavy lifting of running containers without any UI, it's a king of intermediary between the user and the container itself. 

They can be a convenient way to manage the container environment, but they can also introduce some security vulnerabilities. Many daemons run with rood privileges :unamused:. In linux systems root acts as a superuser, with administrative access, this makes dameons an good target for hackers who want to gain control of your containers and infiltrate the host.

**Podman** allows regular user to run containers wihtout interacting with a root-owned daemon, by going rootless, users can create, run, and manage container without requiring admin privileges. Aditionally, podman launches each container with a security-enchanged linux [(SELinux)](https://www.redhat.com/en/topics/linux/what-is-selinux) label, giving administrator more control over what resources and capabiltiies are provided to the proccesses of a container.

Wihtout a damon, how does podman manage containers?

Podman uses a [systemd](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/chap-managing_services_with_systemd?extIdCarryOver=true&sc_cid=701f2000001OH7EAAW) to make updates and keep containers running in the background. By integrating systemd and **podman**, you can generate control units to the container and run them with systemd automatically enabled. Users can manage their own repositories on the system, as well as systemd unit to control the automatic starting and management of their own containers. Allowing users to manage their own resources, and their containers running rootlessly.

Podman also deploys a RESTful API to manage containers. With the REST API, you can call **podman** from platforms such as cUrl, Postman or any Rest Client. 

I've created a simple [GitHub Repo](https://github.com/rafaelherik/hello-podman) with a step by step to install podman desktop. I hope you enjoy it.

