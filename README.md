<div align="center">

# Homelab Documentation :rocket:

This GitHub account serves as documentation for everything in my homelab.

I follow a multi-step setup approach, which is why there are multiple repositories for different stages in this account.

Currently, there are 11 repositories. While this may be confusing for some, it works well for me so far.

Everything is subject to change.

</div>

---

# Table of Contents
- [Setup](#setup)
    - [Why?](#why-did-i-do-it-this-way)
    - [Physical](#physical)
- [Tools](#tools)
    - [Virtualization](#virtualization)
    - [Containerization](#containerization)
    - [Config Management/IaC](#config-managementiac)
    - [Monitoring](#monitoring)
    - [CI/CD](#cicd)
- [Stacks](#stacks)
    - [Base](#base)
    - [Infra](#infra)
    - [Docker](#docker)
    - [k3s](#k3s)
    - [Proxmox Workloads](#proxmox-workloads)

## Setup

The setup is split into stacks: one for Docker hosts, one for K3s... you get the idea. The virtual machines for each stack are managed in the [proxmox-workloads](https://github.com/rz-nord/proxmox-workloads) repository.

Most stacks consist of two separate steps. Due to restrictions in GitLab, each step is in its own repository. Most of the time, the first step uses Ansible to install all prerequisites, while the second step deploys the actual services to the stack.

### Why did I do it this way?
- GitLab currently allows only one repository per project. If I move to another solution in the future, I will restructure this setup.
- Clear separation between stacks.
- Separate host management from service deployment. There’s no need to run through all the code to deploy a new service to a stack.
- GitLab is used instead of Gitea because it is closer to the tools I use at work.
- The Ansible/.env/docker-compose.yml setup ensures that all necessary files are on the host in case something breaks or I decide to stop using CI/CD.

### Physical

The homelab consists of four physical servers with the following roles:

| Server  | OS        | Function                        |
|---------|-----------|---------------------------------|
| node010 | Debian 12 | GitLab/Base Infrastructure      |
| node240 | PBS 3     | Proxmox Backup Server / qDevice |
| node241 | Proxmox 8 | Proxmox Host                    |
| node242 | Proxmox 8 | Proxmox Host                    |

## Tools

### Virtualization
- [Proxmox](https://www.proxmox.com/en/proxmox-virtual-environment)

### Containerization
- [Docker](https://www.docker.com/)
- [K3s](https://k3s.io/)

### Config Management/IaC
- [Ansible](https://github.com/ansible/ansible)
- [Terraform](https://www.terraform.io/)

### Monitoring
- [Prometheus](https://prometheus.io/)
- [Grafana](https://grafana.com/)
- [Loki](https://grafana.com/oss/loki/)

### CI/CD
- [GitLab CE](https://about.gitlab.com/)

## Stacks

### Base
The first layer in the setup. It runs GitLab, the GitLab runners, and some ground-level services like SMB for shares and a registry.
#### Repositories (coming soon)
[base-ansible](https://github.com/rz-nord)
[base-container](https://github.com/rz-nord)

### Infra
This is the second layer. It runs services like monitoring, log aggregation, and notifications. It also deploys a Traefik reverse proxy in a DMZ subnet.
#### Repositories (coming soon)
[infra-ansible](https://github.com/rz-nord)
[infra-container](https://github.com/rz-nord)

### Docker
Docker stack. Provides a runtime environment for Docker containers and services deployed to it.
#### Repositories (coming soon)
[docker-ansible](https://github.com/rz-nord)
[docker-container](https://github.com/rz-nord)

### k3s
K3s stack. Provides a K3s cluster and services deployed to it.
#### Repositories (coming soon)
[k3s-ansible](https://github.com/rz-nord)
[k3s-container](https://github.com/rz-nord)

### Proxmox Workloads
Manages the Proxmox workloads. Everything is created via Terraform, with its state currently stored on a share.
#### Repositories (coming soon)
[proxmox-workloads](https://github.com/rz-nord/proxmox-workloads)
