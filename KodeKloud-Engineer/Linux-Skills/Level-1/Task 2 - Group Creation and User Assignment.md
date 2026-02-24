# Group Creation and User Assignment
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> The system admin team at xFusionCorp Industries has streamlined access management by implementing group-based access control. Here's what you need to do:
>
> a. Create a group named nautilus_admin_users across all App servers within the Stratos Datacenter.
>
> b. Add the user stark into the nautilus_admin_users group on all App servers. If the user doesn't exist, create it as well.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh tony@stapp01

2. create group

    sudo groupadd nautilus_admin_users

3. add user to group, create if needed

    sudo useradd -G nautilus_admin_users stark

4. confirm group exist and user is in group

    cat /etc/group

5. repeat steps 1-4 on the other two servers

6. submit


## My Comments
NA


