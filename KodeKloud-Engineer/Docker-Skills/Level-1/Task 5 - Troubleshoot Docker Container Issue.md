# Troubleshoot Docker Container Issue
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> An issue has arisen with a static website running in a container named nautilus on App Server 1. To resolve the issue, investigate the following details:
> 
> Check if the container's volume /usr/local/apache2/htdocs is correctly mapped with the host's volume /var/www/html.
>
> Verify that the website is accessible on host port 8080 on App Server 1. Confirm that the command curl http://localhost:8080/ works on App Server 1.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh tony@stapp01

2. check container

    sudo docker ps -a

    we will notice its not running
    
3. review container bind mounts and ports to ensure correct mappings since that might also be a concern

    sudo docker inspect nautilus

4. restart stopped container

    sudo docker restart nautilus

5. Ensure running

    sudo docker ps -a

6. ensure website accessible

    curl http://localhost:8080/

7. submit


## My Comments
NA


