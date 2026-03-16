# Change EC2 Instance Type
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> During the migration process, the Nautilus DevOps team created several EC2 instances in different regions. They are currently in the process of identifying the correct resources and utilization and are making continuous changes to ensure optimal resource utilization. Recently, they discovered that one of the EC2 instances was underutilized, prompting them to decide to change the instance type. Please make sure the Status check is completed (if its still in Initializing state) before making any changes to the instance.
>
> 1) Change the instance type from t2.micro to t2.nano for nautilus-ec2 instance.
> 
> 2) Make sure the ec2 instance nautilus-ec2 is in running state after the change.

## Solution

1. login to the test AWS Environment
2. Navigate to ec2 resources, searching ec2 in the top bar will pull it up as a navigation option.
3. Click on 'instances' on left hand pane
4. Ensure your instance is 'running' and 'Status check' has passed, and not 'initializing'
5. click on instance, then use 'instant state' to stop the instance
6. Once fully stopped, might take upto a minute, using the 'action' drop down menu you can 'Change instance type'.
7. Once you have changed the instance type, then start the instance using the 'instant state' drop down menu.
8. Ensure the instant starts and is a 'running' state, and the 'status check' have pasted.
9. submit


## My Comments
NA


