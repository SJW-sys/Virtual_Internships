# Create Security Group
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> the team to execute the migration in gradual phases, ensuring smoother implementation and minimizing disruption to ongoing operations. By breaking down the migration into smaller tasks, the Nautilus DevOps team can systematically progress through each stage, allowing for better control, risk mitigation, and optimization of resources throughout the migration process.
>
> For this task, create a security group under default VPC with the following requirements:
>
> Name of the security group is datacenter-sg.
> 
> The description must be Security group for Nautilus App Servers
>
> Add the inbound rule of type HTTP, with port range of 80. Enter the source CIDR range of 0.0.0.0/0.
>
> Add another inbound rule of type SSH, with port range of 22. Enter the source CIDR range of 0.0.0.0/0.

## Solution
**Important -** While there are more exact commands to make this as quick as possible, I will be as expressive as possible to show a step by step guide with optional verification steps.

1. login to the test AWS Environment
2. Navigate to VPC resources, and open the existing default VPC
3. Open 'Security' > 'Security Groups' on the side pane
4. Click 'Create Security group' in top right
5. Fill out the fourm with the required Information
6. Hit 'Create'
7. Submit task


## My Comments
NA


