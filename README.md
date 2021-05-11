# Docker Stack

This is a guide on how to setup a docker stack on a single linux server and will set the groundwork for you to be able to implement your own services behind a secured reverse proxy easily. 
- [Docker Stack](#docker-stack)
  - [Requirements](#requirements)
  - [Disclaimer](#disclaimer)
  - [Guide](#guide)
    - [1. Update and Prep your Linux Server](#1-update-and-prep-your-linux-server)
    - [2. Install Docker on your machine.](#2-install-docker-on-your-machine)
    - [3. Install Docker Compose on your machine](#3-install-docker-compose-on-your-machine)
    - [4. Make a user to run docker](#4-make-a-user-to-run-docker)

## Requirements

  1. A computer (Server) running Linux. I use Ubuntu Server 20.04.1, But it's really your choice, so long as it can run the latest docker. 
  
## Disclaimer

  This is a guide to exposing a home server to the web. This comes with security risks, and I am not resonsible for any attacks that happen on your network. While this guide will cover some things that you can use to mitigate attacks on your server, it is not foolproof, and I highly reccomend having additional security measures in place, such as a PHYSICAL firewall. 

## Guide
  ### 1. Update and Prep your Linux Server

  <br/>

  There are tons of great guides in order to setup a linux server, update all the packages, resize the LVM's etc. This is all personal preference, so instead I'll just link you to a resource that I've used in the past. Since this is a single instance of a server, I will not be using `ansible` though that is how I typically would provision a server. 

  [TechnoTim - Before I do anything on linux, I do this first...](https://youtu.be/ZsjK4VDopiE)

  ### 2. Install [Docker](https://docs.docker.com/engine/install/) on your machine. 
  <br/>

  > Check the link if you are not installing on `Ubuntu 20.04.1` for your installation instructions.  

  <br/>
  
  1. Update your repositories:
              
       ```bash
       sudo apt-get update
       ```

       
  2. Install the needed packages to allow for a repository to be used over https:

        ```bash
        sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
        ```

  3. Add Docker's Official GPG Key:
  
        ```bash
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
        ```

  4. Set up the `stable` repository. There are other repositories, but for the purposes of this guide we are going to be using the `stable` branch:

        ```bash
         echo \
         "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https:// download.docker.com/linux/ubuntu \
         $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null      
        ```
  5. Install Docker Engine:
        
        ```bash 
        sudo apt update
        ```
        ```bash
        sudo apt install docker-ce docker-ce-cli containerd.io
        ```

  ### 3. Install [Docker Compose](https://docs.docker.com/compose/install/) on your machine
  <br/>
  
  >At the time of writing, the stable version is `1.29.1` please check the official documentation for the latest version. 

  <br/>

  1. Download the current stable release of Docker Compose:

        ```bash
        sudo curl -L "https://github.com/docker/compose/releases/download/1.29.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
        ```
  2. Apply executable permissions on that binary:
        
        ```bash
        sudo chmod +x /usr/local/bin/docker-compose
        ```
  ### 4. Make a user to run docker
  <br/>

  > If you installed Ubuntu Server, the user that was created on installation is sufficient, or if you'd like to create another user follow these steps

  <br/>

  1. Add a new user

        ```bash
        sudo adduser ${USERNAME}
        ```
  2. Give that user sudo permissions
        
        ```bash
        sudo usermod -aG sudo ${USERNAME}
        ```
  3. Setup SSH Key based authentication