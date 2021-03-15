+++
title = "Deploy Microsoft AD"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3. </b>"
+++

**Contents:**
- [AWS Managed Microsoft Active Directory](#aws-managed-microsoft-active-directory)

#### AWS Managed Microsoft Active Directory

In order to **simulate on-premises DNS** infrastructure, we will use **AWS Managed Microsoft Active Directory** service.

1. Login to the **AWS Console** and navigate to the **Directory Service console**. In the find a service search field, type **Directory Services**.
2. Make sure you are choosing the right region. Look at the upper right hand corner of the screen and switch to the your region if you are in a different region. (Here we use Asia Pacfic (Tokyo))
3. If this is the first time you are opening the Directory Services in this region, you’ll be prompted with a welcome screen. Select **“AWS Managed Microsoft AD”** and click on **Set up directory**.
4. In the next screen, select **“AWS Managed Microsoft AD”** and click **Next**.

![Deploy MAD](../../../images/1/5-mad.png?width=90pc)

5. In the **Enter Directory Information** screen, enter the following information:
   - For **Edition**: select **Standard Edition**.
   - **Directory DNS name**: onprem.example.com [Make this DNS name **unique** from your other directories so you can establish trusts in the future if required.]
   - **Directory NetBIOS name**: onprem [Make this NetBIOS **unique** from your other directories as well if you need establish trusts in the future if required.]
   - **Directory Description**: This is to simulate the on-prem AD.
   - **Admin password**: Use a password you can remember. You will use this in future labs. 
   {{% notice info %}}
   Please also review the password complexity requirements outlined on the screen.
   {{% /notice %}}
   - **Confirm password**: Confirm the password again
   - Click **Next**.

![Deploy MAD](../../../images/1/5-mad2.png?width=90pc)

6. For the **VPC and subnets**, please select the **HybridDNS-VPCStack** that you created above and select the two private subnets **Private subnet 1A** and **Private subnet 2A**.
7. After selecting the **VPC and Subnets**, Click **Next**.

![Deploy MAD](../../../images/1/5-mad3.png?width=90pc)

8. On the **Review & create** screen, review the settings and click on **Create Directory**.

![Deploy MAD](../../../images/1/5-mad4.png?width=90pc)

9.  The directory will take about 20 minutes to create. During this time, AWS is provisioning two Windows servers, and promoting them to be Active Directory domain controllers for the AD forest that you specified. This AD forest will be a new AD forest.
10.  The process will be complete when you see the status field turn to **Active**. Once the directory is created, you can see the details by clicking on the **Directory ID**. The two **DNS IP addresses** that are listed are the IP addresses of the elastic network interfaces (ENI) that have been placed in your availability zones to communicate to the **AWS Managed Microsoft AD Domain Controllers**.

![Deploy MAD](../../../images/1/5-mad5.png?width=90pc)
