# RHEL Upgrade Validation & Operations

## Overview

Completing the Leapp upgrade is not the final step.

After the server reboots, automated validation confirms that the target RHEL version is running correctly and that the server is ready to return to normal operations.

## Post-Upgrade Validation

The validation process checks areas such as:

* RHEL version
* Server availability
* Network connectivity
* Filesystem status
* Required services
* Application processes
* Package status
* Security agents
* Monitoring agents
* System health

## Validation Flow

```text
Leapp Upgrade
      |
      v
Server Reboot
      |
      v
Post-Upgrade Checks
      |
      +---- OS Version
      +---- Services
      +---- Network
      +---- Security
      +---- Monitoring
      +---- Application
      |
      v
Upgrade Result
```

## Upgrade Result

Each server should produce a clear result:

```text
SUCCESS
  |
  +-- Upgrade completed
  +-- Validation passed

or

FAILED / ATTENTION REQUIRED
  |
  +-- Upgrade or validation issue
  +-- Requires investigation
```

## Operations Handoff

Once validation is successful, the server can be returned to normal operations.

The operations team can then review:

* Jenkins job result
* Server upgrade status
* Validation results
* Exceptions or warnings
* Servers requiring follow-up

## Handling Failures

If validation identifies an issue, the server should be treated as requiring investigation rather than automatically being marked successful.

Possible actions include:

* Review Jenkins/Ansible output
* Review system logs
* Check affected services
* Engage application or platform owners
* Remediate the issue
* Perform additional validation

## Architecture Principle

**Upgrade success means both the OS upgrade and post-upgrade validation have completed successfully.**

This provides a clear separation between:

**Upgrade Execution → Technical Validation → Operational Handoff**
