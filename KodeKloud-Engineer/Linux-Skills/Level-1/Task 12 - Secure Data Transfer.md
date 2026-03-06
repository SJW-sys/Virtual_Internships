# Secure Data Transfer
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> A Nautilus developer has stored confidential data on the jump host within Stratos DC. To ensure security and compliance, this data must be transferred to one of the app servers. Given developers lack direct access to these servers, the system admin team has been enlisted for assistance.
>
> Copy /tmp/nautilus.txt.gpg file from jump server to App Server 3 placing it in the directory /home/app.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. review file

    ls -al /tmp/nautilus.txt.gpg

2. transfer

    scp /tmp/nautilus.txt.gpg banner@stapp03:/home/app

3. connect to remote system

    ssh banner@stapp03

4. verfiy file

    ls -al /home/app/nautilus.txt.gpg

5. submit


## My Comments
NA


