# Ansible Playbook: Update Package Manager Cache (APT / YUM / DNF)

## Overview
This Ansible playbook updates the package manager cache across multiple Linux distributions.
It automatically detects the target operating system and runs the appropriate cache update
command for APT, YUM, or DNF.

The playbook is designed for mixed Linux environments and continues execution even if
a cache update fails on any host.

## Supported Operating Systems
- Ubuntu / Debian (APT)
- Red Hat Enterprise Linux 7 (YUM)
- Red Hat Enterprise Linux 8 and above (DNF)

## Playbook Details
- Hosts: All (*)
- Privilege Escalation: Enabled (become: yes)
- Become Method: sudo/dzdo
- Remote Temporary Directory: /tmp
- Error Handling: ignore_errors enabled to prevent playbook failure

## Tasks Description
- Updates APT cache on Debian-based systems
- Updates YUM cache on RHEL 7 systems
- Updates DNF cache on RHEL 8+ systems
- Uses conditional logic based on OS family and major version

## Use Cases
- Pre-task before OS patching or package installation
- Routine system maintenance
- Automation in heterogeneous Linux environments
- CI/CD pipeline preparation
- It also can use for **AWX / Tower / enterprise environments**

## How to Run
ansible-playbook -i hosts --ask-pass --become --ask-become-pass  pre_patch_test.yml -e "ansible_user=username"

## Requirements
- Ansible installed on control node
- SSH access to target hosts
- Sudo privileges on managed nodes
- Fact gathering enabled

## Notes
- ignore_errors is intentionally used to avoid interruptions in large environments.
- Suitable for automation workflows where cache updates are non-critical.

👤 Author  
**Sandeep Reddy Bandela**  
Linux | Ansible | Automation
---