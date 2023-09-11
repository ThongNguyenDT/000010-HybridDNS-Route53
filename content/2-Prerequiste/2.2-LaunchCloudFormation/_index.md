---
title : "Initialize CloudFormation Template"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

#### Initialize CloudFormation Template

In this step, you will build the network infrastructure in AWS. In this section, you'll leverage the template from **AWS Quick Start** to build a secure and high availability (HA) network infrastructure using **AWS CloudFormation**. This is the architecture that will be built from the template.

![Launch CloudFormation](/images/2-Pre/0002.png?featherlight=false&width=45pc)

#### Hands-on with AWS CloudFormation

1. **Login to AWS Management Console**

   - Find **CloudFormation**
   - Select **CloudFormation**

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0001.png?featherlight=false&width=90pc)

2. In the **CloudFormation** interface, select **Create stack**.

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0002.png?featherlight=false&width=90pc)

3. In the **Create stack** interface:

   - **Prepare Template**: Template is ready
   - **Template Source**: **Amazon S3 URL**
   - **Amazon S3 URL**: [https://aws-quickstart.s3.amazonaws.com/quickstart-microsoft-rdgateway/templates/rdgw-master.template](https://aws-quickstart.s3.amazonaws.com/quickstart-microsoft-rdgateway/templates/rdgw-master.template)
   - Select **Next**

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0003.png?featherlight=false&width=90pc)

4. Implement stack configuration:

   - In Stack name, enter **HybridDNS**.
   - In **Availability Zones**, select **ap-northeast-1a and ap-northeast-1**.

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0004.png?featherlight=false&width=90pc)

5. Perform Network configuration:

   - In **VPC CIDR, Private Subnet 1 & 2 CIDR, and Public Subnet 1 & 2 CIDR**, keep the default values.
   - In **Allowed Remote Desktop Gateway External Access CIDR**, enter **0.0.0.0/0**.

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0005.png?featherlight=false&width=90pc)

   > **Note:** The warning notice highlights that this configuration allows any IP to remote into the RDP port of the EC2 instance, which is not secure for production.

6. In **Amazon EC2 configuration** step:

   - In **Key Pair Name**, select the previously created Key Pair (hybrid-**DNS**).
   - In **Remote Desktop Gateway Instance Type**, keep the default value (t2.large).
   - In **Number of RDGW Hosts**, keep the default value (1).
   - In **Admin User Name**, keep the default value (StackAdmin).
   - **Admin Password**, set an easy-to-remember password for you.

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0006.png?featherlight=false&width=90pc)

   > **Note:** The note provides additional information about the RDGW hosts and the use of AutoScaling groups for availability and scalability.

7. For other options, keep the default value and select Next.

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0007.png?featherlight=false&width=90pc)

8. Select **Next**.

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0008.png?featherlight=false&width=90pc)

9. On the Review HybridDNS screen, check the settings again. Select the two checkboxes and select **Create Stack**.

   ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0009.png?featherlight=false&width=90pc)

10. The template takes about 15 minutes to complete. In the meantime, we'll take a look at what the CloudFormation template will create. After completing the stack initialization, the stack state will change to **CREATE_COMPLETE**.

    ![Launch CloudFormation](/images/2.2-LaunchCloudFormation/00010.png?featherlight=false&width=90pc)

11. View **Output** of the newly created Stack.
