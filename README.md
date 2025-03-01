<div align="center">

# Homelab documentation :rocket:

This github-account is my attempt at documenting everything i do in my homelab.

I follow a multi-step setup approach, this is why there are multiple repos for multiple stages in this account.

In its current form there are 11 repos. While this may be confusing for some, it works well for me so far.

Everything is subject to change.

</div>

# Table of content
- [Setup](#setup)
- [Tools](#tools)

## Setup

### Physical
At the moment the setup consists of 4 physical servers.
| Server | OS | Function | 
| --- | --- | --- |
| node010 | debian12 | Gitlab/base-infra |
| node240 | PBS | Proxmox Backup Server / qDevice| 
| node241 | Proxmox 8 | Proxmox Host |
| node242 | Proxmox 8 | Proxmox Host |

### Network
Networking is configured through unifi

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
