# Enable Termination Protection for EC2 Instance
## Task
**Important -** Please note that these task can have slight variation such as usernames, filepaths, files, etc

> As part of the migration, there were some components created under the AWS account. The Nautilus DevOps team created one EC2 instance where they forgot to enable the termination protection which is needed for this instance.
>
> An instance named devops-ec2 already exists in us-east-1 region. Enable termination protection for the same.

## Solution

1. login to the test AWS Environment
2. Navigate to ec2 resources, searching ec2 in the top bar will pull it up as a navigation option.
3. Click on 'instances' on left hand pane
4. Open instance, use "action" drop down menu to select "Change termination (deletion) protection" and enable the feature.
5. submit


## My Comments
NA


