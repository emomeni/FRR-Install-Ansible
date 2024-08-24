# Ansible Playbook: Install FRR (Free Range Routing) on Ubuntu Servers

This Ansible playbook automates the installation of the Free Range Routing (FRR) package on Ubuntu servers. FRR is a network routing software suite that provides protocol support for BGP, OSPF, IS-IS, and more. This playbook handles updating package indexes, installing prerequisites, adding the FRR repository, and installing the FRR package.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Variables](#variables)
- [Handlers](#handlers)
- [Verification](#verification)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Introduction

This playbook performs the following tasks:

1. Updates the package manager cache.
2. Installs required dependencies (`apt-transport-https`, `gnupg`).
3. Adds the official FRR repository and GPG key.
4. Installs the FRR package.
5. Ensures the FRR service is started and enabled.

## Prerequisites

- Ansible installed on your local machine or control node.
- SSH access to the target Ubuntu servers.
- Sudo privileges on the target servers for the user running the playbook.
- The target servers must be running a supported version of Ubuntu.

## Installation

1. Clone this repository or download the playbook file:

   ```bash
   git clone https://github.com/yourusername/ansible-install-frr.git
   cd ansible-install-frr
```
2. Ensure your inventory file is set up correctly. Update the `inventory` file with the list of target Ubuntu servers.

3. (Optional) Modify the `install_frr.yaml` playbook file to suit your environment, especially if using different versions or repositories.
