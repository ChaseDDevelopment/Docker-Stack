# Docker Stack

This is a guide on how to setup a docker stack on a single linux server and will set the groundwork for you to be able to implement your own services behind a secured reverse proxy easily. 
- [Docker Stack](#docker-stack)
  - [Requirements](#requirements)
  - [Disclaimer](#disclaimer)
  - [Guide](#guide)
    - [1. Install Docker on your machine.](#1-install-docker-on-your-machine)
    - [2. Install Docker Compose on your machine](#2-install-docker-compose-on-your-machine)
    - [3. Make a user to run docker under,](#3-make-a-user-to-run-docker-under)

## Requirements

  1. A computer (Server) running Linux. I use Ubuntu Server 20.04.1, But it's really your choice, so long as it can run the latest docker. 
  
## Disclaimer

  This is a guide to exposing a home server to the web. This comes with security risks, and I am not resonsible for any attacks that happen on your network. While this guide will cover some things that you can use to mitigate attacks on your server, it is not foolproof, and I highly reccomend having additional security measures in place, such as a PHYSICAL firewall. 

## Guide

  ### 1. Install [Docker](https://docs.docker.com/engine/install/) on your machine.

    1. `sudo apt-get update`

    2. `sudo apt-get install \
          apt-transport-https \
          ca-certificates \
          curl \
          gnupg \
          lsb-release`

  ### 2. Install [Docker Compose](https://docs.docker.com/compose/install/) on your machine

  ### 3. Make a user to run docker under, 