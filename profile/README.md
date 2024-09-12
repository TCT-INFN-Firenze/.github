# Organization Setup Guide
This guide explains how to set up a development environment from a freshly formatted computer, including setting up Git, SSH keys, Docker, and SSH tunneling for remote access.

---

## Table of Contents
1. [User Setup](#user-setup)
2. [Software Installation](#software-installation)
3. [Virtual Environment Setup](#virtual-environment-setup)
4. [Docker Setup](#docker-setup)
5. [SSH Key Setup](#ssh-key-setup)
6. [SSH Tunneling](#ssh-tunneling)
7. [Troubleshooting](#troubleshooting)

---

## User Setup

### Add User to Sudoers List

Log in as `root` and add the current user to the sudoers list:
```bash
su
sudo adduser <username> sudo
sudo reboot
```

---

## Software Installation
Install the necessary software:
- **Pip**, **Git** and **Vim**:
  
  Run the following commands to install Pip, Git, Vim, and Python virtual environment tools:
  ```bash
  sudo apt-get install python3-pip git-all vim python3.11-venv
  ```
  

This GitHub Organization is meant to manage the code for the Transient Current Technique experimental setup developed by the Florence Group of INFN.

The repositories allow to
* Run servers with API to control HV, Motors and a Camera
* Remotely set the most relevant Camera parameters, save a snapshot, and make a fast measurement of the laser sport size
* Remotely move the Motors and set the relevant parameters
* Remotely set and read HV

The content of this organization is currently Private. 

If you want to access the repositories, please contact fabio.davolio@fi.infn.it
