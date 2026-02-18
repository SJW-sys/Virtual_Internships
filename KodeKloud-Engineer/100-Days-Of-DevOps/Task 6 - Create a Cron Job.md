# Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> The Nautilus system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in Stratos DC on a set schedule. Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below:
>
> a. Install cronie package on all Nautilus app servers and start crond service.
>
> b. Add a cron */5 * * * * echo hello > /tmp/cron_text for root user.

# Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh tony@stapp01

2. Install cron

    sudo yum install -y cronie

3. start the crond service

    sudo systemctl start crond

4. (optional) check crond service is running

    sudo systemctl status crond

5. add cron task for root user

    sudo crontab -e

    add the following line:

    */5 * * * * echo hello > /tmp/cron_text

6. (optional) check cron setup

    sudo crontab -l

7.  repeat steps 1-6 with correct logins for the other 2 app servers, when done, submit.

# My Comments
NA
