---
layout: splash
permalink: /vm-setup/
title: ""
excerpt: >
  <br /> 
hidden: false
header:
  overlay_color: "#fafbffff"
  overlay_image: "/assets/images/EBPF_logo.png"
  image: "/assets/images/EBPF_logo.png"
---
#### IISWC Tutorial 2025(October 12, 2025)
# Setting up new VM
The [link](https://console.cloud.google.com/compute/instances?cloudshell=false&project=ucr-ursa-major-socal-lab) to VM instances.

## Machine configuration

- Naming convention:
- Region: `us-central1 (Iowa)`
- Zone: `Any`
- `E2` will probably be enough
- `medium` preset

## OS and storage

- Image needs to be changed:
  - Operating system: `Ubuntu`
  - Version: `Ubuntu 24.04 LTS Minimal` - `x86/64`

## Equivalent Code
```cmd
gcloud compute instances create initial-setup-test --project=ucr-ursa-major-socal-lab --zone=us-central1-a --machine-type=e2-medium --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=default --metadata=enable-osconfig=TRUE --maintenance-policy=MIGRATE --provisioning-model=STANDARD --service-account=351843763492-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/trace.append --create-disk=auto-delete=yes,boot=yes,device-name=initial-setup-test,disk-resource-policy=projects/ucr-ursa-major-socal-lab/regions/us-central1/resourcePolicies/default-schedule-1,image=projects/ubuntu-os-cloud/global/images/ubuntu-minimal-2404-noble-amd64-v20250828,mode=rw,size=10,type=pd-balanced --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --labels=goog-ops-agent-policy=v2-x86-template-1-4-0,goog-ec-src=vm_add-gcloud --reservation-affinity=any && printf 'agentsRule:\n  packageState: installed\n  version: latest\ninstanceFilter:\n  inclusionLabels:\n  - labels:\n      goog-ops-agent-policy: v2-x86-template-1-4-0\n' > config.yaml && gcloud compute instances ops-agents policies create goog-ops-agent-v2-x86-template-1-4-0-us-central1-a --project=ucr-ursa-major-socal-lab --zone=us-central1-a --file=config.yaml
```

# Setting up new user

`sudo` is required for some of these commands. In case of problem this command might help `sudo usermod -a -G google-sudoers $USER`.

- install vim: `sudo apt install vim`

## Adding new user
`useradd -m -s /bin/bash ebpftutorial`

- issues can be seen `cat /etc/issue`

## sudo

- `cd /etc/sudoers.d`
- `vim ebpftutorial`
- paste `ebpftutorial ALL=(root) NOPASSWD: ALL`

## Switch to new user
`su - ebpftutorial`

## Setting up key
- `cd ~ebpftutorial && mkdir .ssh && cd .ssh`
- `vim authorized_keys`
- Add key
- `chmod -Rv 0700 .`
- `chown -Rv ebpftutorial .`

## Setting Password
- `passwd ebpftutorial`
- set safe password (at least 8 character)

to enable password login changed `/etc/ssh/sshd_config`

## Notes
- environemntal variables in /etc/profile.d
- IPs are not gonna be the same after reset

# Snapshot

# Questions

- Ubuntu is 22.04. Why not 24.04?
