# Copy File to Docker Container
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> The Nautilus DevOps team possesses confidential data on App Server 3 in the Stratos Datacenter. A container named ubuntu_latest is running on the same server.
> 
> Copy an encrypted file /tmp/nautilus.txt.gpg from the docker host to the ubuntu_latest container located at /usr/src/. Ensure the file is not modified during this operation.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh banner@stapp03

2. (optional) review running docker containers on host

    sudo docker ps

3. check file permissions on host

    ls -al /tmp/nautilus.txt.gpg

4. copy host file into container

    sudo docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src

4. Validate file exist in container, and file permissions align (they should)

    sudo docker exec ubuntu_latest ls -al /usr/src

5. submit

## My Comments
I rarely have had to copy files into docker machines in my experience, used ' sudo docker --help ' to fined the ' cp ' command is valid with docker, and dug in the help menu with cp ' sudo docker cp --help '.

