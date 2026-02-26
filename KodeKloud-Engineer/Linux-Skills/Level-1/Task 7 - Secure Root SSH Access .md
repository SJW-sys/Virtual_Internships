# Secure Root SSH Access
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> Following security audits, the xFusionCorp Industries security team has rolled out new protocols, including the restriction of direct root SSH login.
>
> Your task is to disable direct SSH root login on all app servers within the Stratos Datacenter.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh tony@stapp01

2. Disable root login in sshd config

    sudo vi /etc/ssh/sshd_config

    change the existing line for root login to show

    PermitRootLogin no

    ensure to write out (save) and exit

3. reload sshd

    sudo systemctl reload sshd

4. repeat step 1-3 on the other two app servers

5. submit

## My Comments
NA


