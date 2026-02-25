# Service User Creation without Home Directory
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> In response to the latest tool implementation at xFusionCorp Industries, the system admins require the creation of a service user account. Here are the specifics:
>
> Create a user named jim in App Server 3 without a home directory.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh banner@stapp03

2. create user without home dir

    sudo useradd -M jim

3. validate user exist and no home dir

    cat /etc/passwd
    ls -al /home/

4. submit

## My Comments
NA


