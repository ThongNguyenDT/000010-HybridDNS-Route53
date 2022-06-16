---
title : "Microsoft AD Deployment"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Deploy Microsoft AD

To emulate **DNS** on-premise, we will use **AWS Directory Service** to deploy **AWS Managed Microsoft Active Directory** in two private subnets created by CloudFormation as shown below :


![RDGW](/images/2-Pre/0004.png?featherlight=false&width=45pc)


1. Log in to **AWS Console** and access the Directory Service console through the search box and find Directory Services.

- Make sure you have selected the correct Region. Notice in the left corner of **AWS Console** and select the correct Region you need (Here we are selecting ap-southeast-1)


![RDGW](/images/4-AD/0001.png?featherlight=false&width=90pc)

2. If you are accessing Directory Services for the first time in your region, you will be taken to the initial welcome screen. Expand the left sidebar and select Directories.


   - Select **Set up directory**.

![RDGW](/images/4-AD/0002.png?featherlight=false&width=90pc)

3. Select **Directory types**, select **AWS Managed Microsoft AD**

![RDGW](/images/4-AD/0003.png?featherlight=false&width=90pc)

4. In the Enter Directory Information page, enter the following information:
   
   - In **Edition**: select **Standard Edition**.

   - In **Directory DNS name**: onprem.example.com (this **DNS** name must be unique among your directories).

   - In **Directory NetBIOS name**: onprem (this **NetBIOS** name must be unique among your directories).


![RDGW](/images/4-AD/0004.png?featherlight=false&width=90pc)

5. Continue configuration

   - In **Directory Description**: This is to simulate the on-prem AD.

   - In **Admin Password**: Use a password you can remember. Please note the password complexity requirements listed on the screen.

   - In **Confirm password**: Re-enter the password again.

   - Select **Next**.

![RDGW](/images/4-AD/0005.png?featherlight=false&width=90pc)

6. In Choose VPC and subnets, select the VPC Hybrid**DNS**-VPCStack that we created earlier and two private subnets, Private subnet 1A and Private subnet 2A. Then select Next.

![RDGW](/images/4-AD/0006.png?featherlight=false&width=90pc)

7. On the Review & create screen, review the settings and select Create Directory.

![RDGW](/images/4-AD/0007.png?featherlight=false&width=90pc)

8. Directory will take about 20 minutes to create. During this time, AWS will provision two **Windows** servers and elevate them to **Active Directory** domain controllers for the AD forest you specified. This AD forest will be a new AD forest. The process will be complete when you see the status change to Active

![RDGW](/images/4-AD/0008.png?featherlight=false&width=90pc)

9. Once the directory has been created, you can view the details by clicking on the Directory ID. The two **DNS** IP addresses listed are the IP addresses of **elastic network interfaces** (ENI) that have your availability zone set to communicate with **AWS Managed Microsoft AD Domain Controllers**.

![RDGW](/images/4-AD/0009.png?featherlight=false&width=90pc)