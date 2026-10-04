# RHEL Upgrade Automation

## Overview

The upgrade workflow uses **Jenkins, Ansible, Python, and Leapp** to provide a repeatable process for RHEL major-version upgrades.

The operations team interacts primarily with the Jenkins job, while the automation handles the underlying workflow.

## Automation Flow

```text
Operations Team
       |
       v
Jenkins Upgrade Job
       |
       v
Ansible Playbook
       |
       +---- Inventory
       |
       +---- Upgrade Inputs
       |
       +---- Package Exclusions
       |
       v
Pre-Upgrade Checks
       |
       v
Leapp
       |
       v
RHEL Major Version Upgrade
       |
       v
Reboot
       |
       v
Post-Upgrade Validation
```

## Jenkins

Jenkins provides a simple execution interface for the operations team.

Typical inputs include:

* Server inventory
* Server list
* Source / target upgrade information
* Package exclusion list
* Upgrade execution option

The objective is to make the process:

**Select → Configure → Upgrade**

rather than requiring manual execution on each server.

## Ansible

Ansible orchestrates the upgrade workflow across the selected servers.

High-level responsibilities include:

* Validate inventory
* Perform pre-checks
* Prepare the server
* Process upgrade inputs
* Apply required exclusions
* Invoke the Leapp workflow
* Reboot the server
* Run post-upgrade checks
* Report the result

## Python

Python can be used for supporting automation logic such as:

* Processing upgrade inputs
* Validating parameters
* Handling package exclusion information
* Supporting workflow decisions
* Producing structured results

Python is used as a supporting component rather than replacing Ansible or Leapp.

## Leapp

Leapp performs the RHEL major-version upgrade.

The automation controls the surrounding workflow while Leapp handles the operating-system upgrade process.

```text
Ansible
   |
   v
Leapp Assessment
   |
   v
Leapp Upgrade
   |
   v
Reboot
   |
   v
Target RHEL Version
```

## Package Exclusion

Package exclusions are provided as controlled inputs for servers where specific components require special handling.

Examples include:

* Python-related components
* Security agents
* Apache-related components
* Application-specific packages

The exclusion capability allows the same automation framework to support different server/application requirements.

## Automation Objective

The design reduces manual intervention while maintaining control over the upgrade process.

The desired operational experience is:

```text
Update Inventory
      ↓
Select Servers
      ↓
Define Exclusions
      ↓
Click Upgrade
      ↓
Monitor Job
      ↓
Review Results
```

This creates a consistent and repeatable approach for upgrading multiple RHEL servers.
