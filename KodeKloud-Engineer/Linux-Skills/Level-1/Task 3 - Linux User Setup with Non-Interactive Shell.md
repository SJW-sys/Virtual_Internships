# Linux User Setup with Non-Interactive Shell
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> To accommodate the backup agent tool's specifications, the system admin team at xFusionCorp Industries requires the creation of a user with a non-interactive shell. Here's your task:
> 
> Create a user named kirsty with a non-interactive shell on App Server 1.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh tony@stapp01

2. create user with non-interactive shell

    sudo useradd -s /sbin/nologin kristy

3. (optional) verify user creation

    cat /etc/passwd

4. submit

## My Comments
Had a strange platform issue where this failed, redid the lab same way and it passed.


