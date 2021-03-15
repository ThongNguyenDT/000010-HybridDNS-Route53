+++
title = "Build Network with CloudFormation"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1. </b>"
+++

The first step to building a Windows infrastructure in AWS is to build out the network infrastructure. You will leverage an [**AWS Quick Start**](https://aws.amazon.com/quickstart/architecture/rd-gateway/) to build out a secure highly available network infrastructure show below.

AWS Quick Starts leverage AWS CloudFormation which is AWS’s Infrastructure as Code (IaC) service that allows you to create infrastructure based upon a template (written in YAML or JSON). The template is uploaded to the CloudFormation service and itc creates the infrastructure described in the template.

![Overview Diagram](../../../images/1/0-diagram.png?width=40pc)

**Contents:**
- [1.1.1. Creating a Key Pair](#111-creating-a-key-pair)
- [1.1.2. Running the Quick Start CloudFormation Template](#112-running-the-quick-start-cloudformation-template)
- [1.1.3. Securing the Environment](#113-securing-the-environment)

#### 1.1.1. Creating a Key Pair
In order to secure access to your EC2 instances, AWS uses private/public key technology and this takes the form of an AWS key pair. With Windows instances, the key pair is used to obtain the administrator password via the Amazon EC2 console. In this section, you will create the key pair.

1. Login to the **AWS Console** and navigate to the **EC2 Management console**. To get to the **EC2 management console**, in the find a service search box, type **EC2**.
2. Make sure you are choosing the right region. Look at the upper right hand corner of the screen and switch to the your region if you are in a different region. (Here we use Asia Pacfic (Tokyo))
3. On the left menu bar, select **Key Pairs**.
4. Select **Create key pair**.
5. In the **Create Key pair** screen,
   - For **Name**, enter "hybrid-dns". (Or any name that suitable for you)
   - For **File format**, check pem.
   - Press **Create key pair**.
![Create Key Pair](../../../images/1/1-keypair.png?width=90pc)
6. **Important**: AWS downloads the private key portion of the key pair. It will have a name like **hybrid-dns.pem**. Be sure to save the PEM file and record the location of this file. You will use this file later to decrypt the administrator password. You won’t be able to re-download this file later.

#### 1.1.2. Running the Quick Start CloudFormation Template
In this section, you are going to get hands-on experience with AWS CloudFormation to build out the base network infrastructure.

1. Login to the **AWS Console** and navigate to the **CloudFormation (CFN) console**. In the find a service search box, type **CloudFormation**.
2. Make sure you are choosing the right region. Look at the upper right hand corner of the screen and switch to the your region if you are in a different region. (Here we use Asia Pacfic (Tokyo))
3. Click on **Create stack** > **With new resources (standard)**
4. In the **Create stack** screen, enter the values as shown below and click on **Next**.
   - **Prepare Template**: Template is ready
   - **Template Source**: Amazon S3 URL
   - **Amazon S3 URL**:  
```
https://aws-quickstart.s3.amazonaws.com/quickstart-microsoft-rdgateway/templates/rdgw-master.template
```
Or download the template below:
{{%attachments style="orange" title="CloudFormation Template" pattern=".*(template)"/%}}

![Create Stack](../../../images/1/2-createstack.png?width=90pc)

5. For the **Stack name**, enter HybridDNS.
6. For the **Availability Zones**, select ap-northeast-1a and ap-northeast-1c.
7. For **VPC CIDR**, Private Subnet 1 & 2 CIDR, and Public Subnet 1 & 2 CIDR, leave the default values.
![Create Stack](../../../images/1/2-createstack2.png?width=90pc)

8. For the **Allowed Remote Desktop Gateway External Access CIDR**, enter 0.0.0.0/0. 
{{% notice warning %}}
This will allow any IP to be able to RDP into the RDP gateway.  
This is not a secure configuration and it is not recommended for a production deployment. We will go back and tighten this down after the CloudFormation stack has been deployed. 
{{% /notice %}} 
9.  In the **Key Pair Name**, select the Key Pair that you created earlier (e.g. hybrid-dns).  
10. For the **Remote Desktop Gateway Instance Type**, leave the default (t2.large).  
11. For the **Number of RDGW Hosts**, leave the default (1).  
{{% notice note %}}
Please note that the above diagram shows two RDGW hosts (one in each Availablity Zone (AZ)).  
For the purposes of the lab, we are starting with one RDGW host to reduce the amount of time that the CloudFormation process takes to run. However in the diagram, you can see that the RDGW hosts are deployed into an AutoScaling group.  
After the CloudFormation process finishes, you can examine the AutoScaling group. Autoscaling groups are a key service that can provide scalability and availability to your application.
{{% /notice %}}
12. For **Admin User Name**, leave the default (StackAdmin).  
13. For **Admin Password**, set a password that you will remember. Note, the password complexity requirements (8 characters minimum, and needs letters, numbers, and symbols).  
14. For **Domain DNS Name**, leave the default (example.com).  
15. For the remaining options, leave the default values and click **Next**.
![Create Stack](../../../images/1/2-createstack3.png?width=90pc)

16. On the **Configure Stack Options**, review the options. Click **Next**.
17. On the **Review HybridDNS** screen, review the settings. Check the two checkboxes and click **Create Stack**.
![Create Stack](../../../images/1/2-createstack4.png?width=90pc)

{{% notice info %}}
The template takes about 15 minutes to complete. During this time, we will review what the CloudFormation template is creating.  
Once stack creation is completed, the status on the stack creation will change to **CREATE_COMPLETE**.
{{% /notice %}}

![Create Stack](../../../images/1/2-createstack5.png?width=90pc)

#### 1.1.3. Securing the Environment
We are going to tighten the security of the RDGW access.

1. Login to the **AWS Console** and navigate to the **EC2 Management console**. To get to the **EC2 management console**, in the find a service search box, type **EC2**.
2. Make sure you are choosing the right region. Look at the upper right hand corner of the screen and switch to the your region if you are in a different region. (Here we use Asia Pacfic (Tokyo))
3. In the left hand menu, click **Security Groups**.
4. Select the checkbox for the security group that has a description, **“Enable RDP access from the Internet”**
5. In the bottom area, select the **Inbound** tab.
6. Press **Edit**.
![Secure Environment](../../../images/1/3-secureenvironment.png?width=90pc)
7. Click the **Delete** next to the rule that contain the **Port Range, 3391** to delete the rule
8. Click the **Delete** next to the rule that contain the **Port Range, 443** to delete the rule
9. On the **RDP rule** in the **Source** column, click the dropdown and select **“My IP”**
10. On the **ICMP rule** in the **Source** column, click the dropdown and select **“My IP”**
11. Press **Save**
![Secure Environment](../../../images/1/3-secureenvironment2.png?width=90pc)

{{% notice note %}}
When securing your application, you want to make sure to only open the ports that your application needs.  
In this example, you removed port 3391 and 443, since you will not be using those ports in these labs. Also, you have locked down the access so that the RDP and ICMP connections can only originate from your public IP address.  
Some customers lock down access so that RDP and ICMP connections can only originate from the public IP addresses of their corporate network.
{{% /notice %}}