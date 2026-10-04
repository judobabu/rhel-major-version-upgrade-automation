# RHEL Upgrade Planning & Workflow

## Overview

The upgrade process starts with planning and pre-checks before any changes are made to the server.

The goal is to identify potential upgrade issues early and provide a controlled path from the existing RHEL version to the target major version.

## Planning

Before an upgrade, the team identifies:

* Source RHEL version
* Target RHEL version
* Server inventory
* Application owner
* Server purpose
* Maintenance window
* Required package exclusions
* Backup / recovery readiness
* Post-upgrade validation requirements

## High-Level Workflow

```text id="w6m7qz"
Inventory
   |
   v
Pre-Checks
   |
   v
Leapp Assessment
   |
   v
Review Findings
   |
   v
Resolve Issues / Define Exclusions
   |
   v
Upgrade
   |
   v
Reboot
   |
   v
Validation
```

## Pre-Upgrade Checks

Typical checks include:

* Confirm server is reachable.
* Confirm supported source and target RHEL versions.
* Check disk space.
* Check package and repository configuration.
* Check system health.
* Check required services.
* Review Leapp pre-upgrade findings.
* Confirm backup or recovery readiness.
* Identify packages requiring special handling.

## Package Exclusions

Some workloads may have packages or components that require special handling during the upgrade.

The automation provides an input for controlled exclusions.

For example:

```text id="w0v5bk"
Server
  |
  +-- Standard Packages
  |
  +-- Python Components      → Exclude if required
  |
  +-- Security Agent         → Exclude if required
  |
  +-- Apache Components      → Exclude if required
```

The exclusion list is reviewed before the upgrade rather than being applied automatically to every server.

## Upgrade Readiness

A server should proceed only when the pre-upgrade assessment is acceptable and known issues have been addressed.

```text id="v3a2sd"
              Pre-Check
                 |
          +------+------+
          |             |
        Ready        Issues Found
          |             |
          v             v
       Upgrade       Remediate /
                     Review
```

## Architecture Principle

**Identify upgrade risks before making changes to the operating system.**

The planning and pre-check stage provides a controlled entry point into the automated upgrade process.
