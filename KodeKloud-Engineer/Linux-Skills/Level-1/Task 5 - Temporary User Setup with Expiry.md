# Temporary User Setup with Expiry
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> As part of the temporary assignment to the Nautilus project, a developer named javed requires access for a limited duration. To ensure smooth access management, a temporary user account with an expiry date is needed. Here's what you need to do:
> 
> Create a user named javed on App Server 2 in Stratos Datacenter. Set the expiry date to 2027-02-17, ensuring the user is created in lowercase as per standard protocol.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh steve@stapp02

2. create user

    sudo useradd -e 2027-02-17 javed

3. validate

    sudo chage -l javed

4. submit


## My Comments
NA


