---
title: "Installing Docker"
permalink: /eBPF-tutorial/docs/install-docker/
excerpt: "Installing Docker for Setting up the workloads"
last_modified_at: 2025-09-01T08:48:05-04:00
toc: false
---

## Step 4: Install Docker

To set up Docker for the workloads, follow these steps:

### For Ubuntu/Debian-based Systems:
1. **Update the system**
Update the system and install the required dependencies for Docker:

```bash
sudo apt update
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

2. **Add Docker’s official GPG key:**

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

3. **Set up the Docker stable repository:**

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

4. **Update the apt package list to include Docker:**

```bash
sudo apt update
```

5. **Install Docker:**

```bash
sudo apt install -y docker-ce
```

6. **Start Docker and verify that it's running:**

```bash
sudo systemctl start docker
sudo docker --version
```

This will show the installed Docker version, confirming that Docker has been successfully installed.

## Step 5: Install Python 3.10 and Create Virtual Environment (Optional)

If you need Python 3.10 to set up a virtual environment, follow these steps:

### Install Python 3.10 and the venv package:

```bash
sudo apt install -y python3.10-venv
```

Once installed, you can create a virtual environment using the following command:

```bash
python3.10 -m venv myenv
```

Replace `myenv` with your desired virtual environment name.

Once these steps are complete, Docker will be ready for running containers, and Python 3.10 will be available for creating virtual environments.