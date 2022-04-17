---
title: "Why I Decided to Develop Playback"
date: 2017-02-28
draft: false
authors: ["jiasir"]
categories: ["2017"]
series: ["OpenStack"]
tags: ["OpenStack"]
description: "Since March 2015 I decided to develop a new automated deployment tool for OpenStack called the [Playback](http://playback.jiasir.io). Because I tried almost all popular tools and these tools are not suitable for me."
---

Since March 2015 I decided to develop a new automated deployment tool for OpenStack called the [Playback](http://playback.jiasir.io). Because I tried almost all popular tools and We need a low learning cost, flexible, production-oriented high-availability level automated build tool. Below is a simple comparison of some open source solutions:

* [Juju solutions for OpenStack](https://jujucharms.com/openstack)
* [OpenStack Autopilot](https://www.ubuntu.com/cloud/openstack/autopilot)
* [puppetlabs-openstack](https://github.com/puppetlabs/puppetlabs-openstack)
* [openstack-ansible](https://github.com/openstack/openstack-ansible)
* [Kolla](https://github.com/openstack/kolla)
* [RDO(Packstack)](https://rdoproject.org)
* [TripleO](https://wiki.openstack.org/wiki/TripleO)

##### Juju solutions for OpenStack
Juju is a good tool for provisioning and orchestration, but bad to deploy OpenStack. In the initial version there are a lot of software bugs that make the deployment process not very smooth. I spent a lot of time on it to fix bugs of charm, The secondary development cost is relatively high, and the refresh of the relations cannot be customized.

##### OpenStack Autopilot
Autopilot handles every aspect of your cloud both during installation, expansion, and everyday operations. The deployment process is very simple. You need a MAAS Server and a machine for the OpenStack Autopilot. All the deployment process is automated. Enjoy it:) Also we can try OpenStack Autopilot for free, but we need to purchase Ubuntu Advantage when we use more than 10 machines.

##### puppetlabs-openstack
puppetlabs-openstack is a puppet deployment module for OpenStack, it is my first used. At that time(about two years ago) also does not support a highly available deployment, but at present only support to Kilo version. Its deployment environment is very complex, and cannot be combined random deployment. 

##### openstack-ansible
openstack-ansible is an official OpenStack project which aims to deploy production environments from source in a way that makes it scalable while also being simple to operate, upgrade, and grow. It is based on the LXC, and the project develops very fast! It has become the official deployment guide by default. In the current version, the deployed architecture is not very flexible yet.

##### Kolla
Kolla provides Docker containers, Ansible playbooks to deploy OpenStack on baremetal or virtual machine, and Kubernetes templates to deploy OpenStack on Kubernetes to meet Kolla's mission. Bug! Bug! Bug! You can hardly succeed! and inflexible!

##### RDO(Packstack)
Packstack based on puppet and through a answer file for deployment. At that time(about two years ago) it cannot be able to add more nodes to your OpenStack cloud later, because you will refresh the deployment of other components deployed. it is inflexible and you have to under the RedHat systems.

##### TripleO
TripleO is a program aimed at installing, upgrading and operating OpenStack clouds using OpenStack's own cloud facilities as the foundations - building on nova, neutron and heat to automate fleet management at datacentre scale (and scaling down to as few as 2 machines). You can use TripleO in RDO-land. The complexity is very high, and it has very low maintainability.

#### And why Playback?
[Playback](http://playback.jiasir.io) is an OpenStack provisioning and orchestration library that all of the OpenStack components can be automated deployment with high availability on Ubuntu based operating system(Xenial and trusty) as a pythonic way. Playback 0.4.0 and later will support the new command line interface. I made it since March 2015, according to the deployment of simplicity and flexibility, made great improvements for production. At first the implementation is based on the Ansible playbooks, but the playbook configuration and maintenance has brought a lot of work. So it was changed to a more lightweight way and more friendly(the python library). Import the playback library and write your own scripts to deploy OpenStack for developers or use the command line directly for operations. [FastForward](https://nofdev.github.io/fastforward/)(an ultimate DevOps platform) based on playback(0.3.8) to provision an OpenStack currently.

* [Docs](http://playback.jiasir.io)
* [Source](https://github.com/jiasir/playback)
