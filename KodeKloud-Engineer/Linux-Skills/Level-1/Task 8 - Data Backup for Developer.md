# Data Backup for Developer
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> Within the Stratos DC, the Nautilus storage server hosts a directory named /data, serving as a repository for various developers non-confidential data. Developer javed has requested a copy of their data stored in /data/javed. The System Admin team has provided the following steps to fulfill this request:
>
> a. Create a compressed archive named javed.tar.gz of the /data/javed directory.
>
> b. Transfer the archive to the /home directory on the Storage Server.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh natasha@ststor01

2. navigate to desired end target for file

    cd /home

3. compress the desired data into location with the correct name

    sudo tar -czf javed.tar.gz /data/javed

4. validate file exist

    ls -al

5. submit


## My Comments
NA


