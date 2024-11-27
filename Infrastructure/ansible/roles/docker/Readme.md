# Role: Docker Installation
This Ansible role automates the installation and configuration of Docker on your system. It checks if Docker is already installed, removes any conflicting Docker-related packages, and installs Docker cleanly.

## How to Use
Run the Playbook To execute this role, include it in your playbook and run the playbook on your target system.

Setting Up for the First Time If you are setting up Docker for the first time, you need to set the new_installation variable to true. This tells the role to perform a fresh installation of Docker.

Example command:

```bash
ansible-playbook playbook.yml -e "new_installation=true"
```

Running the Playbook for Subsequent Tasks If Docker is already installed and you are running other tasks, you can omit the new_installation variable, or set it to false.

Example command:

```bash
ansible-playbook playbook.yml
```

## What This Role Does
For New Installations (new_installation=true):

Checks if Docker is already installed.
Removes any conflicting Docker-related packages (e.g., docker.io, docker-compose, containerd).
Downloads and installs the official Docker Engine.
Adds the current user to the Docker group for easier access.
For Existing Systems (new_installation=false or not set):

Skips Docker installation tasks.

## Requirements
Supported OS: Debian-based systems (e.g., Ubuntu) or compatible Linux distributions.
Ansible must be installed on the control machine.
SSH access to the target machine(s).

## Notes
Always set new_installation=true for the first-time setup to ensure proper installation.
If you encounter issues with Docker, rerun the playbook with new_installation=true to perform a clean reinstallation.