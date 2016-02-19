# Before You Begin

Before you start using AWS with Calm, you need to deploy Calm from our AWS AMI. To do so, you’ll need the following:

* An AWS account with valid credentials

* An IAM user account with the following permissions and access:

    * EC2 Full Permissions

    * IAM Read Only Access

To know more about creating an IAM user on AWS, go to [http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html).

* The Access Key ID and the Secret Access Key for your IAM user account with AWS. 

## Setting up an IAM User Account

We have developed a script that creates an IAM user along with the necessary permissions and a security group for deploying a Calm AMI. This script can be used with AWS CloudFormation to create an IAM user. 

The script can be downloaded from: <link>

To create an IAM user with the AWS CloudFormation template, do the following:

1. Download the script from:

2. Select **CloudFormation** from the AWS dashboard > **Management Tools**. 

3. Select **Create Stack**. 

4. Select **Select a sample template** under **Choose a template**, and choose the script to be uploaded from the directory that you saved the script in. 

## Instance Requirements

In order to use the Calm Community AMI seamlessly, it is advisable to configure the instance according to the following requirements:

* **Disk Space**: A minimum of 40 GB. 100 GB of disk space is advisable. 

* **Shutdown Behaviour**: Stop
