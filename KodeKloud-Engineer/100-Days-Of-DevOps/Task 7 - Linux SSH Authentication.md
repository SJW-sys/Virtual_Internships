# Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> The system admins team of xFusionCorp Industries has set up some scripts on jump host that run on regular intervals and perform operations on all app servers in Stratos Datacenter. To make these scripts work properly we need to make sure the thor user on jump host has password-less SSH access to all app servers through their respective sudo users (i.e tony for app server 1). Based on the requirements, perform the following:
>
> Set up a password-less authentication from user thor on jump host to all app servers through their respective sudo users.

# Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. check for existing keys for thor in default location

    ls -al /home/thor/.ssh/

2. None found, generate keys using ed25519 for more modern standards (and better security). Will use higher KDF  (via -a option) to increase key resistance to brute force attacks, trade off is slower verification. Change from default 16 to 100

    ssh-keygen -t ed25519 -a 100 -f ~/.ssh/id_ed25519

Normally we would setup a passphrase, but task ask for password-less ssh, so we will assume (since there is no way to get clarity) we will not setup a passphrase

3. Copy to each server individual using below command. This command directly appends your .pub key to the ~/.ssh/authorized_keys file, if it does not exist, nor the .ssh directory, it will create the files/dir with the correct permissions.

    ssh-copy-id -i ~/.ssh/id_ed25519.pub tony@stapp01

4. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh tony@stapp01

If you were successful to login without a password, everything is working. If it failed, you may need to modify /etc/ssh/sshd_config to allow passkey authentication. The task does not ask us to prevent password login, so we will not disable it.

5. (optional) you have already verified the key is working, when you logged in and no password was prompted, but you can confirm the ssh key is setup in the correct via by checking with the below command.

    cat /home/tony/.ssh/authorized_keys

6. Complete steps 3-4, for the other two app servers.

7. Submit.

# My Comments
NA
