# SElinux Installation and Configuration
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> Following a security audit, the xFusionCorp Industries security team has opted to enhance application and server security with SELinux. To initiate testing, the following requirements have been established for App server 2 in the Stratos Datacenter:
>
> Install the required SELinux packages.
>
> Permanently disable SELinux for the time being; it will be re-enabled after necessary configuration changes.
>
> No need to reboot the server, as a scheduled maintenance reboot is already planned for tonight.
>
> Disregard the current status of SELinux via the command line; the final status after the reboot should be disabled.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh steve@stapp02

2. Install SELinux

    sudo dnf install -y selinux-policy-targeted policycoreutils policycoreutils-python-utils

3. Backup config files

    sudo cp /etc/selinux/config /etc/selinux/config.backup

4. Edit SELinux Config

    sudo vi /etc/selinux/config

    Change 'SELINUX' to the following

    SELINUX=disabled

5. Check SELinux status, this will show the current running status and the config file status (what will be set on reboot)

    sestatus

6. submit

## My Comments
NA


