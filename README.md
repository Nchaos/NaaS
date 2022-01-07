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

1. Navigate to Actions
2. Select the AVH_Deploy_Manual workflow
3. Click 'Run workflow'
4. Complete the form
5. Click 'Run workflow' at the bottom of the form

### Deployment Notes
The ARM template deployment can be customized by overriding the default parameter values. Please review the template for a full understanding of the default values. There are also some features that are not configurable at this time. The items below are of particular interest.

* Virtual machines (VM) deployed in all environments except for 'prod' are configured to auto-shutdown at 07:00PM Central Standard Time as a safeguard against unnecessary costs during development/testing.
* The Network Security Group (NSG) must allow outbound traffic to the internet. This is necessary to allow /bash_scripts/autopart.sh to be retrieved for execution on the VMs as part of the custom script extension that formats and mounts the data disk. The example parameter files in the /azure folder include the required NSG rule to allow HTTPS traffic. Any input supplied to the 'networkSecurityGroupRules' parameter should contain this rule at a minimum to ensure the deployment is successful.
* The NSG is configured to allow SSH from all IP addresses if no input is provided for the 'networkSecurityGroupSshSourceIP' parameter. A single IP or a comma-separated list of IPs may be supplied to this parameter to limit SSH as needed.
* A bastion host may be deployed as a method of securely accessing the VMs deployed with this template. However, this is not enabled by default. To enable this part of the deployment, set the 'deployBastion' parameter to either 'true' or 'True'.



## Status of Azure Virtualization Host Deployment
[![AVH_Deploy_Azure](https://github.com/Nchaos/NaaS/actions/workflows/avh_deploy.azure.yml/badge.svg?branch=master)](https://github.com/Nchaos/NaaS/actions/workflows/avh_deploy.azure.yml)