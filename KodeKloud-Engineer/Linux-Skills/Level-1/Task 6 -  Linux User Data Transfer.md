# Linux User Data Transfer
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> Due to an accidental data mix-up, user data was unintentionally mingled on Nautilus App Server 3 at the /home/usersdata location by the Nautilus production support team in Stratos DC. To rectify this, specific user data needs to be filtered and relocated. Here are the details:
>
> Locate all files (excluding directories) owned by user john within the /home/usersdata directory on App Server 3. Copy these files while preserving the directory structure to the /beta directory.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. Connect to target server, login details found in the 'company' wiki. (In a real world this would be in a vault,or you be accessing via your own assigned identity, not a shared identity.)

    ssh banner@stapp03

2. review data in question and generate data counts owned by john

    ls -al /home/usersdata 
    sudo find /home/usersdata -type f -user john | wc -l
    sudo find /home/usersdata -type f | wc -l

3. review target location in question and generate data counts currently owned by john in location

    ls -al /beta
    sudo find /beta -type f -user john | wc -l

4. copy the files to new location preserving structure, 'dir#' used as a substitute for actual directory names

    sudo find /home/usersdata -type f -user john -exec cp --parents {} /beta \;

5. review target location in question has expected copies and data counts matching step 1 (subtracking/adding anything from step 2). because we did not need to preserve permissions (--preserve=ownership when you copy) you will be looking at all files

    ls -al /beta
    sudo find /beta/home/usersdata -type f | wc -l

6. submit

## My Comments
I did need to do some research to determine the best way to transfer data from a targeted user, as I was unfamiliar with how to do this. Compared some stack overflow,reddit and other post against an AI generated answer, which I tested into a temp folder I created then removed upon validating expected outcome.


