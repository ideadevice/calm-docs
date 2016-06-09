# Before You Begin

Before you start using AWS with Calm, you need to deploy Calm from our AWS AMI. To do so, you’ll need the following:

* An AWS account with valid credentials

* An IAM user account with the following permissions and access:

    * EC2 Full Permissions

    * IAM Read Only Access

!!! tip "Note"
	To know more about creating an IAM user on AWS, go to [this AWS Documentation page](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html).

* The Access Key ID and the Secret Access Key for your IAM user account with AWS. 

## Setting up an IAM User Account

We have developed a script that creates an IAM user along with the necessary permissions and a security group for deploying a Calm AMI. This script can be used with AWS CloudFormation to create an IAM user. 

The script can be downloaded from: <link>

To create an IAM user with the AWS CloudFormation template, do the following:

* Download the script from:

2. Select **CloudFormation** from the AWS dashboard > **Management Tools**. 

3. Select **Create Stack**. 

4. Select **Select a sample template** under **Choose a template**, and choose the script to be uploaded from the directory that you saved the script in. 

## Instance Requirements

In order to use the Calm Community AMI seamlessly, it is advisable to configure the instance according to the following requirements:

* **Disk Space**: A minimum of 40 GB. 100 GB of disk space is advisable. 

* **Shutdown Behaviour**: Stop

# Launching the Calm Community AMITo deploy Calm from your AWS AMI, do the following:* Login to your AWS account. 2. Select **EC2** from your AWS dashboard. 3. Select **Launch Instance**.!!! tip "Note"    You might want to choose your AWS Region to ensure that the instance you’re launching is in the region of your choice.* Select **Community AMIs** and type Calm in the Search bar. 5. Select the **Calm AMI** from the search results according to the version that you’d like to launch. 6. Select the **Instance Type** as **m4.large** from the list. 7. Select **Next: Configure Instance Details**8. Configure the instance based on your requirements. You can opt for an **Availability Zone** of your choice. Make sure that **IAM Role** is set to **None** and **Shutdown Behaviour** is set to **Stop**. 9. Select **Next: Add Storage** and opt for a **Volume Size** of at least **40 GB**. !!! tip "Note"    It is best to launch an instance with a disk size of **100 GB**.* Select **Next: Tag Instance** and tag your instance, if required. 11. Select **Next: Configure Security Group**. 12. Select and set **HTTP** and **HTTPS** under **Type**. !!! tip "Note"    **SSH** is preselected as a **Type** by default. **Do not** change this setting. * Select **Review and Launch**. 14. Review all the instance configurations that you’ve set and then select **Launch**. 15. Select an existing key pair, create a new key pair or choose to proceed without a key pair to connect to this instance. !!! tip "Note"    A key pair is necessary when you’re trying to SSH into the instance that you’ve launched.The launch of your Calm AMI will now be initialized and subsequently launched. You can view this AMI by selecting **EC2** and then **Running Instances** from your AWS dashboard. # Accessing Your Calm AMI

To access your Calm AMI, do the following:

* Select the Calm AMI you launched from the list of **Running Instances** from your **EC2** dashboard. 

* Copy the **Public DNS** and paste it into any web browser and hit **Enter**. This initiates the **Calm Setup Wizard**.

The **Calm Setup Wizard** will now take you through creating a Calm account and setting up your Calm instance for use. 