# Environment Setup Guide

Follow the steps below to set up your working environment for this project.

---

## Requirements

This guide assumes you're using **Ubuntu** installed **natively** (no virtual machines or WSL). The setup has only been tested and verified on local Ubuntu installations. The **minimum recommended version** of Ubuntu is **20.04.**

---

## Setup Steps

### 1. Install Git

Open the terminal (**Ctrl+Alt+T**) and run the following commands to install Git:

```bash
sudo apt-get update
sudo apt-get install git-all
```

---

### 2. Clone the Repository

Use the `git clone` command to download the repository to your local machine:

```bash
git clone git@github.com:TCC-ROS/ros-noetic.git
```

#### Don’t have an SSH key?

If you see an SSH-related error when cloning, follow these steps:

1. Generate a new SSH key:

   ```bash
   ssh-keygen
   ```

   Just press `ENTER` when prompted.

2. Navigate to your SSH directory:

   ```bash
   cd ~/.ssh/
   ```

3. Open and copy the contents of the public key:

   ```bash
   gedit id_rsa.pub
   ```

4. Go to [GitHub → Settings → SSH and GPG keys](https://github.com/settings/keys) and paste the copied key to add a new SSH key.

---

### 3. Install Docker

Navigate into the cloned repository and go to the Docker setup folder:

```bash
cd ros-noetic/docker
```

If you **don’t have an NVIDIA GPU**, run the following script to install Docker:

```bash
./install_docker.bash
```

>  If the Docker installation fails, it's likely due to an issue with your APT configuration. This would need to be resolved independently.

---

### Terminal Navigation Tips

Here are some helpful commands for navigating the terminal:

| Command         | Description                         |
|----------------|-------------------------------------|
| `ls`           | List directory contents             |
| `cd [dir]`     | Change to specified directory       |
| `cd ..`        | Move one level up                  |
| `cd ../../`    | Move two levels up                 |
| `cd ~`         | Go to your home directory           |

Examples:
- From `/usr/local/share` to `/usr/local`:
  ```bash
  cd ..
  ```
- From `/usr/local/share` to `/usr/local/src`:
  ```bash
  cd ../src
  ```

---

### 4. Build Docker Environment

Docker allows you to build and run software in isolated environments. To build the Docker image for this project, run:

```bash
sudo ./build_docker.sh
```

If the build fails, try running it again. If it continues to fail, open the `Dockerfile` and **comment out lines 59 and 61**, then retry.

---

### 5. Run Docker Container

Once the Docker image is built, start the container with:

```bash
sudo ./run_docker.sh
```

---

### 6. Into Docker Container

After running the Docker container in one terminal, you need to run the following command in each new terminal to enter the container environment:

```bash
sudo ./into_docker.sh
```

---
