---
title : "Microsoft AD Deployment"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Deploy Microsoft AD

To set up **DNS emulation** on-premises, we will utilize the **AWS Directory Service** to deploy **AWS Managed Microsoft Active Directory** in two private subnets created by CloudFormation, as illustrated below:

![RDGW](/images/2-Pre/0004.png?width=45pc)

1. Log in to the **AWS Console** and navigate to the Directory Service console by using the search box and selecting Directory Services.
   
   Ensure that you have chosen the appropriate Region. Check the top left corner of the **AWS Console** and select the desired Region (For instance, we're selecting ap-southeast-1).
   
   ![RDGW](/images/4-AD/0001.png?width=90pc)

2. If this is your first time accessing Directory Services in your region, you will be directed to the initial welcome screen. Expand the left sidebar and click on Directories.
   
   - Choose **Set up directory**.
   
   ![RDGW](/images/4-AD/0002.png?featherlight=false&width=90pc)

3. Select **Directory types** and then choose **AWS Managed Microsoft AD**.
   
   ![RDGW](/images/4-AD/0003.png?featherlight=false&width=90pc)

4. On the "Enter Directory Information" page, provide the following details:
   
   - For **Edition**, select **Standard Edition**.
   
   - For **Directory DNS name**, use `onprem.example.com` (ensure this **DNS** name is unique among your directories).
   
   - For **Directory NetBIOS name**, use `onprem` (ensure this **NetBIOS** name is unique among your directories).
   
   ![RDGW](/images/4-AD/0004.png?featherlight=false&width=90pc)

5. Proceed with the configuration:
   
   - For **Directory Description**, use `this to simulate the on-prem AD`.
   
   - Set an **Admin Password** that you can remember. Note the password complexity requirements provided on the screen.
   
   - Confirm the password by entering it again.
   
   - Click on **Next**.
   
   ![RDGW](/images/4-AD/0005.png?featherlight=false&width=90pc)

6. In the "Choose VPC and subnets" section, select the VPC named **HybridDNS-VPCStack** that we previously created, along with two private subnets: **Private subnet 1A** and **Private subnet 2A**. Then, proceed to the next step.
   
   ![RDGW](/images/4-AD/0006.png?featherlight=false&width=90pc)

7. On the "Review & create" screen, carefully review the settings, and then click on **Create Directory**.
   
   ![RDGW](/images/4-AD/0007.png?featherlight=false&width=90pc)

8. The creation of the directory will take approximately 20 minutes. During this time, AWS will provision two **Windows** servers and promote them to **Active Directory** domain controllers for the specified AD forest. This forest will be a new AD forest. The process will be marked as complete when the status changes to Active.
   
   ![RDGW](/images/4-AD/0008.png?featherlight=false&width=90pc)

9. Once the directory has been successfully created, you can view its details by clicking on the Directory ID. The two **DNS** IP addresses listed represent the IP addresses of **elastic network interfaces** (ENI) associated with your availability zone for communication with **AWS Managed Microsoft AD Domain Controllers**.
   
   ![RDGW](/images/4-AD/0009.png?featherlight=false&width=90pc)
