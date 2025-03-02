<div align="center">

# Homelab documentation :rocket:

This github-account is my attempt at documenting everything i do in my homelab.

I follow a multi-step setup approach, this is why there are multiple repos for multiple stages in this account.

In its current form there are 11 repos. While this may be confusing for some, it works well for me so far.

Everything is subject to change.

</div>

---

# Table of content
- [Setup](#setup)
- [Tools](#tools)
- [Repos](#repos)

## Setup

I split the setup in stacks. One for my docker-hosts, one for k3s... you get the gist.
The virtual machines for each stack are stored in the [proxmox-workloads](https://github.com/rz-nord/proxmox-workloads) repostitory.
Most stacks contain two seperate steps. Due to restrictions in gitlab each step is in its own repository. The most of the time the first step runs ansible to install all prerequisites, while the second step actually deploys services to the stack.

### Why did i do it this way?
- Gitlab currently only allows one repostitory per project. If i maybe move to another solution in the future this will be restructured
- I want to have separation between my stacks
- I want to handle the hosts and the services seperateley. Theres no need to run through all the code if i simply want to deploy a new service to a stack
- Gitlab is used instead of gitea because its closer to the tools i use at work

### Physical
At the moment the setup consists of 4 physical servers.
| Server | OS | Function | 
| --- | --- | --- |
| node010 | debian12 | Gitlab/base-infra |
| node240 | PBS 3 | Proxmox Backup Server / qDevice| 
| node241 | Proxmox 8 | Proxmox Host |
| node242 | Proxmox 8 | Proxmox Host |

### Network
Networking is configured through unifi.

## Tools

### Virtualization
 - Proxmox

### Containerization
 - docker
 - k3s

### Configmanagement/IaC
 - ansible
 - terraform

### Monitoring
 - prometheus
 - grafana
 - loki

### CI/CD
 - Gitlab CE 

## Repos

### Proxmox workloads
[proxmox-workloads](https://github.com/rz-nord/proxmox-workloads)

This repository and its gitlab pipeline manage the proxmox workloads. Everything is created via terraform wich state is stored on a share for now.
