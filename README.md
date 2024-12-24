# Docker Installation Guide for Ubuntu (EC2 or Local Machine)

This guide explains how to install Docker on an Ubuntu machine, whether it's an **AWS EC2 instance** or a **local Ubuntu machine**. Follow the steps below to set up Docker and start using containers.

## Prerequisites

- An Ubuntu machine (AWS EC2 instance or local Ubuntu installation).
- SSH access to the EC2 instance or terminal access to your local machine.

## Steps to Install Docker

### 1. Update the Package Index

Run the following command to update the package index:

```bash
sudo apt-get update
```
### 2. Install Required Dependencies
- Install the dependencies required to allow apt to use repositories over HTTPS:

```bash
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```
### 3. Add Docker’s Official GPG Key
- Add Docker’s official GPG key to your system:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
### 4. Add Docker Repository
- Add Docker’s official repository to your APT sources:

```bash
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```
### 5. Update the Package Index Again
- After adding Docker’s repository, update the package list again:

```bash
sudo apt-get update
```
### 6. Install Docker
- Install Docker:

```bash
sudo apt-get install docker.io
```
### 7. Start and Enable Docker Service
- Start the Docker service and enable it to run on boot:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```
### 8. Verify Docker Installation
- Check if Docker is installed and running by verifying its version:

```bash
sudo docker --version
```
- You should see Docker’s version information, confirming that Docker is installed correctly.

### 9. Run Docker Without sudo (Optional)
- If you'd like to run Docker commands without sudo, add your user to the Docker group:

```bash
sudo usermod -aG docker $USER
```
- Then, log out and log back in, or run the following command to apply the group changes:

```bash
newgrp docker
```
- Now you should be able to run Docker commands without needing sudo.

### 10. Test Docker
- Finally, test Docker by running the hello-world container:

```bash
docker run hello-world
```
- If everything is set up correctly, Docker will pull the hello-world image and run it, displaying a success message.

## Conclusion
- Docker is now installed and running on your Ubuntu machine! You can start using Docker to build, run, and manage containers.
