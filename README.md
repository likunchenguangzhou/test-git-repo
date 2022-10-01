# **Build resilient applications using AWS Backup**

This lab is provided as part of **[AWS Innovate For Every Application Edition](https://aws.amazon.com/events/aws-innovate/apj/for-every-app/)**

Click [here](https://github.com/phonghuule/aws-innovate-fea-2022) to explore the full list of hands-on labs.

ℹ️ You will run this lab in your own AWS account. Please follow directions at the end of the lab to remove resources to avoid future costs.

## Introduction
The purpose of this lab is to teach you how to use [AWS backup](https://aws.amazon.com/backup/) to achieve automatic data backup, so as to build resilient applications with well defined data backup strategy.

Create backup of the data is just first step to enhance data resilience. You as data owner must also test these backups to ensure they can be used to recover data. A backup is useless if you are unable to restore your data from it. Testing the restore process after each backup will ensure you are aware of any issues that might arise during a restore down the line.

In this lab, you will create an EC2 Instance as a data source. You will then create a strategy to backup these data sources periodically using AWS Backup, and finally, automate the testing of the restore process as well as cleanup of resources using AWS Lambda.

The skills you learn will help you define a backup and restore plan in alignment with the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc&wa-guidance-whitepapers.sort-by=item.additionalFields.sortDate&wa-guidance-whitepapers.sort-order=desc).

## Goals:
* Set up a Backup Strategy to ensure mission-critical data is being backed up regularly
* Test restoring from EC2 image backups to ensure there are no data recovery issues
* Learn how to automate this process

## Prerequisites:
* An [AWS Account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) that you are able to use for testing, that is not used for production or other purposes.
* An IAM user or role in your AWS account that has Administrator privileges. Launch the CloudFormation Stack to provision resources that will act as data sources.

## Note
NOTE: You will be billed for any applicable AWS resources used if you complete this lab that are not covered in the [AWS Free Tier](https://aws.amazon.com/free/).

## Deploy the Infrastructure and Application
You may refer to the following solution architectual view. You will use AWS CloudFormation to provision resources needed for this lab. As part of this lab, the CloudFormation stack that you provision will create an EC2 Instance, an SNS Topic, and a Lambda Function. You can view the CloudFormation template [here](https://github.com/JerryChenZeyun/Build-resilient-applications-using-AWS-Backup/blob/main/aws-backup-lab.yaml) for a complete list of all resources that are provisioned. This lab will **only work in us-east-1**.

![Solution Architect View](/images/solution-topo.png)
<br /><br />

### Step1: Deploy the Infrastructure
#### 1.1 Log into the AWS console
Sign in to the AWS Management Console as an IAM user who has PowerUserAccess or AdministratorAccess permissions, to ensure successful execution of this lab.

#### 1.2 Deploy the infrastructure using AWS CloudFormation
Click the following button to deploy the stack. [\
![](https://d2908q01vomqb2.cloudfront.net/f1f836cb4ea6efb2a0b1b99f41ad8b103eff4b59/2019/10/30/LaunchCFN.png)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?stackName=WA-Backup-Lab&templateURL=https://aws-innovate-2022-aws-backup-lab.s3.ap-southeast-2.amazonaws.com/aws-backup-lab.yaml)

Under **PARAMETERS**:

1. Select an **AvailabilityZone** to launch the resources in.
2. For **LatestAmiId** leave the default value. This will automatically retrieve the latest AMI ID for Amazon Linux 2.
3. Specify an email address that you have access to for **NotificationEmail**.

Check the box **I acknowledge that AWS CloudFormation might create IAM resources**.

Click CREATE / CREATE STACK.

The stack takes about 2 minutes to create all the resources. Periodically refresh the page until you see that the **STACK STATUS** is in **CREATE_COMPLETE**. Once the stack is in **CREATE_COMPLETE**, visit the **OUTPUTS** section for the stack and note down the **KEY** and **VALUE** for each of the outputs. This information will be used later in the lab.

You can view the simple application running on the instance by visiting the URL specified in the outputs. If you get an error that says “Connection refused”, wait a couple of minutes and try again.

### Step2: Create a Backup Plan
Now you will create a backup strategy by leveraging AWS Backup, a fully managed backup service that can automatically backup data from various data sources such as EC2 Instances, EBS Volumes, RDS Databases, and more. You can view a complete list of supported services [here](https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html#supported-resources).

### Step3: Enable Notification


### Step4: Test Restoration


### Step5: Tear Down








