# ansible01Prov

Ansible playbooks for provisioning a development environment with various tools and software.

## Overview

This repository contains two main Ansible playbooks:

1. **provision.yml** - Main provisioning playbook that installs and configures:
   - Latest version of Golang (from official website)
   - Visual Studio Code with plugins (Go, Python, JavaScript)
   - Google Chrome browser
   - Node.js via npm
   - @conotion/cli via npm
   - WiFi configuration (SSID: CampusStMarc with password: Thunderbolt)
   - Removes previous known WiFi networks

2. **reset_provision.yml** - Reset and provisioning playbook that:
   - Resets the 'student' user (removes and recreates)
   - Runs the main provisioning playbook

## Prerequisites

- Ubuntu/Debian-based Linux system
- Ansible installed (version 2.9 or later)
- sudo/root access
- Internet connection

## Usage

### Run the main provisioning playbook

```bash
ansible-playbook provision.yml
```

This will install all the required software and configure the system.

### Run the reset and provision playbook

```bash
ansible-playbook reset_provision.yml
```

This will reset the 'student' user and then provision all the software.

### Dry run (check mode)

To see what changes would be made without actually making them:

```bash
ansible-playbook provision.yml --check
```

## Configuration

- **ansible.cfg** - Ansible configuration file
- **inventory** - Inventory file defining localhost as the target

## Notes

- The playbooks are designed to run on localhost
- Some tasks may require sudo/root privileges
- WiFi configuration requires NetworkManager to be installed
- VSCode extensions are installed for the 'student' user
- The reset playbook will completely remove and recreate the 'student' user

## Customization

You can customize the following variables in the playbooks:

- `golang_version` - Specific Golang version (defaults to latest)
- `vscode_extensions` - List of VSCode extensions to install
- `wifi_ssid` - WiFi network SSID
- `wifi_password` - WiFi network password
- `student_user` - Username to reset/configure (defaults to 'student')

## License

This project is open source and available under the MIT License.