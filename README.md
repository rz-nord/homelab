<div align="center">

# Homelab Documentation :rocket:

This GitHub account serves as documentation for everything I do in my homelab.

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
- [Repositories](#repositories)
    - [Proxmox Workloads](#proxmox-workloads)

## Setup

I split the setup into stacks: one for my Docker hosts, one for K3s... you get the idea. The virtual machines for each stack are managed in the [proxmox-workloads](https://github.com/rz-nord/proxmox-workloads) repository.

Most stacks consist of two separate steps. Due to restrictions in GitLab, each step is in its own repository. Most of the time, the first step uses Ansible to install all prerequisites, while the second step deploys the actual services to the stack.

### Why did I do it this way?
- GitLab currently allows only one repository per project. If I move to another solution in the future, I will restructure this setup.
- I want a clear separation between my stacks.
- I want to separate host management from service deployment. There’s no need to run through all the code if I just want to deploy a new service to a stack.
- GitLab is used instead of Gitea because it is closer to the tools I use at work.
- The Ansible/.env/docker-compose.yml setup ensures that all necessary files are on the host in case something breaks or I decide to stop using CI/CD.

### Physical

The homelab consists of four physical servers with the following roles:

| Server  | OS       | Function                          |
|---------|---------|----------------------------------|
| node010 | Debian 12 | GitLab/Base Infrastructure      |
| node240 | PBS 3   | Proxmox Backup Server / qDevice |
| node241 | Proxmox 8 | Proxmox Host                    |
| node242 | Proxmox 8 | Proxmox Host                    |

## Tools

### Virtualization
- Proxmox

### Containerization
- Docker
- K3s

### Config Management/IaC
- Ansible
- Terraform

### Monitoring
- Prometheus
- Grafana
- Loki

### CI/CD
- GitLab CE

## Repositories

### Proxmox Workloads
[proxmox-workloads](https://github.com/rz-nord/proxmox-workloads)

This repository, along with its GitLab pipeline, manages the Proxmox workloads. Everything is created via Terraform, with its state currently stored on a shared storage.

