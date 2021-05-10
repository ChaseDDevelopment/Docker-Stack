# Docker-Stack
This is my Docker Stack on my Home Server

## I'm starting with posting my traefik configuration, and will slowly add more services in. 

### Requirements

  1. A computer (Server) running Linux. I use Ubuntu Server 20.04.1, But it's really your choice, so long as it can run the latest docker. 
  
### Disclaimer

  This is a guide to exposing a home server to the web. This comes with security risks, and I am not resonsible for any attacks that happen on your network. While this guide will cover some things that you can use to mitigate attacks on your server, it is not foolproof, and I highly reccomend having additional security measures in place, such as a PHYSICAL firewall. 

### Guide

  1. Install [Docker](https://docs.docker.com/engine/install/) on your machine.

    1. `sudo apt-get update`

    2. ```sudo apt-get install \
          apt-transport-https \
          ca-certificates \
          curl \
          gnupg \
          lsb-release```  

  2. Install [Docker Compose](https://docs.docker.com/compose/install/) on your machine

  3. Make a user to run docker under, 