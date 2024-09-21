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
- [Improvements](#improvements)

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

## Usage
Run the playbook with the following command:
```bash
ansible-playbook -i your_inventory_file install_frr.yaml
```
Replace `your_inventory_file` with the path to your Ansible inventory file.

## Variables
The following variables are defined in the playbook and can be customized:
* `frr_repo_url`: URL of the FRR repository (default: `https://deb.frrouting.org/frr`)
* `frr_repo_key_url`: URL of the FRR repository GPG key (default: `https://deb.frrouting.org/frr/keys.asc`)
* `frr_version`: The version of FRR to install (default: `frr-stable`)

To override these variables, you can pass them directly via the command line:
```bash
ansible-playbook -i your_inventory_file install_frr.yml -e "frr_version=frr-8"
```

## Handlers
* Restart FRR service: This handler restarts the FRR service whenever the FRR package is installed or updated.

## Verification
After running the playbook, you can verify the installation by checking the FRR version:
```bash
vtysh -c "show version"
```
The output should display the installed version of FRR, confirming a successful installation.

## Troubleshooting
* Permission Denied: Ensure the user running the playbook has sudo privileges on the target servers.
* FRR Repository Not Found: Check that the FRR repository URL is correct and accessible from the target servers.
* Service Not Starting: Verify that the frr service is enabled and running using the systemctl status frr command.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Improvements
### Key Changes and Improvements in an updated version of playbook (v2):
* Key Changes and Improvements:
* Compatibility Check Enhancement: Added a version check for Ubuntu to ensure the playbook runs only on compatible versions (18.04 or later).
* Consistency in Task Definition:
* Used with_items instead of loop for installing prerequisites. It provides better readability for simple lists.
* Whitespace for Readability: Added blank lines between tasks and sections to improve readability.
* Tags for Better Control (Optional): Consider adding tags to tasks for more granular control if needed in the future.

### General Improvements in an updated version of playbook (v2):
* Improved error messaging and task descriptions for clarity.
* Kept tasks and variables organized and easy to understand.


# Explanation of the README.md Structure
1. **Introduction**: Brief overview of the playbook's purpose and functionality.
2. **Prerequisites**: Lists the requirements needed before running the playbook.
3. **Installation**: Instructions on how to download and set up the playbook.
4. **Usage**: Provides a command to run the playbook with Ansible.
5. **Variables**: Describes configurable variables used within the playbook.
6. **Handlers**: Lists any handlers defined within the playbook, like service restarts.
7. **Verification**: How to confirm the successful installation of FRR.
8. **Troubleshooting**: Common issues and their potential solutions.
9. **License**: Licensing information for the project.
9. **Improvements**: Changes and Improvements for the ansible playbook in the 2nd version of playbook.

Feel free to modify this `README.md` according to the specific needs and structure of your repository.
