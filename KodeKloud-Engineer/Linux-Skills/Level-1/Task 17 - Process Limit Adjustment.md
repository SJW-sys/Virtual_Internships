# Process Limit Adjustment
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> In the Stratos Datacenter, our application server 1 is encountering performance degradation due to excessive processes held by the nfsuser user. To mitigate this issue, we need to enforce limitations on its maximum processes. Please set the maximum process limits as specified below:
>
> a. Set the soft limit to 1027
>
> b. Set the hard limit to 2027

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh tony@stapp01

2. validate user exist

    id nfsuser

3. Check user current process limits

    sudo -u nfsuser bash -c 'ulimit -a'

4. backup limits config file

    sudo cp /etc/security/limits.conf /etc/security/limits.conf.backup

5. Edit limits.conf File

    sudo vi /etc/security/limits.conf

    Add the following:

    nfsuser    soft    nproc    1027
    nfsuser    hard    nproc    2027

6. Check user current process limits

    sudo -u nfsuser bash -c 'ulimit -a'

7. submit


## My Comments
Had to do some reading on this concept as I was totally unfamilar, one of the more condensed useful resources: https://www.tecmint.com/set-limits-on-user-processes-using-ulimit-in-linux/
the Limits.conf file also has valuable information within it.

