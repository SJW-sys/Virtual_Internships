# Install Docker Packages and start docker services
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> The Nautilus DevOps team aims to containerize various applications following a recent meeting with the application development team. They intend to conduct testing with the following steps:
>
> Install docker-ce and docker compose packages on App Server 1.
> 
> Initiate the docker service.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh tony@stapp01

3. see if docker repo is on server

   yum repolist

3. Add docker repo to server (see resource in the below my comments section)

    sudo dnf -y install dnf-plugins-core
    sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

3. (optional) verify repo on server

   yum repolist

4. (optional) verify you can find the packages

    sudo yum search docker

    you should now see docker-ce and docker-compose-plugin

5. Install required docker packages (or use docker install guide which recommends adding a few other docker packages so you have everything you need in a typical install)

    sudo yum install docker-ce docker-compose-plugin

6. Start service

    sudo systemctl start docker

7. check services is running

    sudo systemctl status docker

8. submit


## My Comments
Resource: https://docs.docker.com/engine/install/centos/
Found and followed the above documentation, limited experience with CentOS and adding repos on it. Most of my experience is in apt with debian, so traditionally installing docker there.


