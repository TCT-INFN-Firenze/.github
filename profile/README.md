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

---

## Virtual Environment Setup
- **Create and Activate a Virtual Environment**:

  After Python is installed, create a virtual environment
  ```bash
  python3 -m venv <name>
  source <name>/bin/activate
  ```
- **Deactivate**

  To deactivate the virtual environment later, simply run:
  ```bash
  deactivate
  ```

---

## Docker Setup

1. **Install Docker and Docker Compose**:

   Follow the [Docker installation guide for Debian](https://docs.docker.com/engine/install/debian/#install-using-the-repository) to install Docker Compose using the apt repository.

2. **Run Docker without `sudo`**:

   Add your user to the Docker group to run Docker without needing `sudo`:
   ```bash
   sudo groupadd docker
   sudo gpasswd -a $USER docker
   newgrp docker
   ```

---

## SSH Key Setup
1. **Check if an SSH Key already exists**:

   Check if you already have and SSH key with the following command:
   ```bash
   ssh-add -l -E sha256
   ```
2. **Generate a New SSH Key** (if needed):

   If no key exists, generate a new one:
   ```bash
   ssh-keygen -t ed25519 -C "github_email@example.com"
   ```

3. **Add the SSH Key to GitHub**:
   - Open GitHub, click on your profile picture, and go to **Settings**.
   - In the **Access** section on the left, click **SSH and GPG keys** and then **New SSH Key**.
   - Title the key and copy the contents of `/home/<user>/.ssh/id_ed25519.pub` into the **Key** field.

---

## SSH Tunneling
1. **Install OpenSSH Server**:

   To enable SSH access to your host computer:
   ```bash
   sudo apt-get install openssh-server
   ```
2. **Configure Router for External Access**:
   - Open your router's settings by typing `192.168.1.1` in your browser.
   - Log in using the router's username and password.
   - Save the device under **Network/LAN/Address Reservation**.
   - Assign a unique external port in **Transmission/NAT/Virtual Servers**.
  
3. **Configure SSH for Remote Connections**:

   Set up passwordless SSH by adding the public key from the connecting machine into the `authorized_keys` file of the machine you are accessing:
   ```bash
   cat ~/.ssh/id_rsa.pub | ssh <remote_user>@<remote_host> "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
   ```

4. **SSH Config File Setup**:

   If you are frequently connecting from a specific machine, create an SSH config file on the connecting computer (`~/.ssh/config`):
   ```text
   Prova
   ```


This GitHub Organization is meant to manage the code for the Transient Current Technique experimental setup developed by the Florence Group of INFN.

The repositories allow to
* Run servers with API to control HV, Motors and a Camera
* Remotely set the most relevant Camera parameters, save a snapshot, and make a fast measurement of the laser sport size
* Remotely move the Motors and set the relevant parameters
* Remotely set and read HV

The content of this organization is currently Private. 

If you want to access the repositories, please contact fabio.davolio@fi.infn.it
