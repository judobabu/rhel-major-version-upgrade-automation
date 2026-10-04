# rhel-major-version-upgrade-automation

# Enterprise RHEL Major Version Upgrade Automation

## Overview

This project presents a high-level approach for automating **RHEL major-version upgrades** across enterprise servers using **Leapp, Ansible, Python, and Jenkins**.

The objective is to make OS upgrades more consistent, repeatable, and easier to operate across a large server inventory while providing pre-checks, controlled package exclusions, upgrade execution, and post-upgrade validation.

## High-Level Workflow

```text
Server Inventory
       |
       v
Jenkins Upgrade Job
       |
       v
Ansible Playbook
       |
       v
Pre-Upgrade Checks
       |
       v
Leapp Assessment
       |
       v
Resolve / Exclude Required Packages
       |
       v
Leapp Upgrade
       |
       v
Server Reboot
       |
       v
Post-Upgrade Validation
```

## Operational Model

The upgrade process is designed to be simple for the operations team:

1. Update the server inventory.
2. Select the required server list.
3. Specify package/component exclusions when required.
4. Start the Jenkins upgrade job.
5. Monitor the upgrade progress.
6. Review the post-upgrade validation results.

The automation handles the underlying Ansible and Leapp workflow.

## Package Exclusions

Some servers may require specific packages or components to be excluded or handled separately during the upgrade.

Examples may include:

* Python-related packages
* Security agent components such as CrowdStrike
* Apache-related packages
* Application-specific packages

The exclusion mechanism allows the upgrade process to be adapted to the requirements of individual server workloads.

## Key Components

| Component  | Purpose                              |
| ---------- | ------------------------------------ |
| Jenkins    | Upgrade job / execution interface    |
| Ansible    | Automation and orchestration         |
| Leapp      | RHEL major-version upgrade           |
| Python     | Supporting automation and logic      |
| Inventory  | Defines target servers               |
| Validation | Confirms server health after upgrade |

## Architecture Principles

* Standardize the OS upgrade process.
* Minimize manual server-by-server activities.
* Perform pre-upgrade checks before changes.
* Allow controlled exclusions where required.
* Use automation for repeatability.
* Validate the server after the upgrade.
* Provide clear upgrade results to the operations team.

## Architecture Highlights

* Designed a repeatable approach for enterprise RHEL major-version upgrades.
* Integrated Jenkins, Ansible, Python and Leapp into a controlled upgrade workflow.
* Reduced manual effort by allowing the operations team to manage upgrades through a Jenkins job.
* Supported server-list/inventory driven execution across multiple systems.
* Added controlled package exclusions for components requiring special handling.
* Included pre-upgrade checks and Leapp assessment before making OS changes.
* Added automated reboot and post-upgrade validation.
* Separated upgrade execution from validation to improve operational control.
* Designed the workflow to support consistent execution, monitoring and troubleshooting.

## Architecture Perspective

This project represents a simplified, high-level enterprise approach to RHEL major-version upgrade automation. The focus is on architecture, automation workflow, operational control and validation rather than production-specific playbooks or proprietary implementation details.

## Scope

This is a **high-level reference architecture** based on an enterprise RHEL upgrade automation approach.

The repository does not contain production playbooks, credentials, internal server information, or proprietary automation code.
