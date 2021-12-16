# NaaS
Development environment for Networking as a Service

## Virtualization Host
The Azure folder contains an Azure Resource Management (ARM) Template and example parameters file that can be used to deploy an Infrastrcture Virtualization Host on Azure running Ubuntu 20.4

## Dev Environments

There are two development environments

### 2spine-2leaf
- This folder contains a multi-vm Vagrantfile that can be used to provision a environment with 2 Spine EOS VMs and 2 Leaf EOS VMs
### 2spine-6leaf
- This folder contains a multi-vm Vagrantfile that can be used to provision a environment with 2 Spine EOS VMs and 6 Leaf EOS VMs


## Usage
The .github/workflows folder contains YAML workflows that are used to deploy the Infrastructure Virtualization Host in multiple Azure environments.

### Automatic Deployments
Deployments will be triggered automatically on pushes to the master branch that contain changes to the any of the following files:

1. Any file in the Azure folder
2. Any of the workflow files

### Manual Deployments
Deployments can be initiated manually using the following steps:

1. Nagivate to Actions
2. Select the AVH_Deploy_Manual workflow
3. Click 'Run workflow'
4. Complete the form
5. Click 'Run workflow' at the bottom of the form

## Status of Azure Virtualization Host Deployment
[![AVH_Deploy_Azure](https://github.com/Nchaos/NaaS/actions/workflows/avh_deploy.azure.yml/badge.svg?branch=master)](https://github.com/Nchaos/NaaS/actions/workflows/avh_deploy.azure.yml)