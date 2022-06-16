---
title : "Create Route 53 Outbound Endpoint"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

#### Create Route 53 **Outbound Endpoint**

As a first step, we will create Route 53 **Outbound Endpoint** to allow **Route 53 Resolver** to forward **DNS** queries with domains hosted outside of Route 53. When you Route 53 **Outbound Endpoint**, AWS will create an **elastic network interface** (ENI) in each **Availability Zones** (AZ) you specify.

![RDGW](/images/2-Pre/0006.png?featherlight=false&width=45pc)


1. Access Route 53 console through the search box and find Route 53.
- Expand the left sidebar, select Outbound Endpoint**s**, and select Create **Outbound Endpoint**

![RDGW](/images/5.1-CreateOE/0001.png?featherlight=false&width=90pc)

2. On the Create **Outbound Endpoint** page, enter the following information:
   - Endpoint name: R53-OutboundEndpoint
   - **VPC in the Region**: HybridDNS-VPCStack-. (This is the VPC created by CloudFormation in the previous section)
   - **Security group for this endpoint**: d-###….#_controllers. (This is the security group that CloudFormation created to protect connections to **AWS Managed Microsoft Active Directory**)

![RDGW](/images/5.1-CreateOE/0002.png?featherlight=false&width=90pc)

3. Configure **IP addresses**

- At **IP address #1:**
  - In **Availability Zone**, select “ap-southeast-1a”
  - In **Subnet**, select “Private subnet 1A”
  - In **IP address**, select “Use an IP address that is selected automatically”
- At **IP address #2:**
  - In **Availability Zone**, select “ap-southeast-1c”
  - In **Subnet**, select “Private subnet 2A”
  - In **IP address**, select “Use an IP address that is selected automatically”

![RDGW](/images/5.1-CreateOE/0003.png?featherlight=false&width=90pc)

3. Finally, select **Create Outbound Endpoint**.

![RDGW](/images/5.1-CreateOE/0004.png?featherlight=false&width=90pc)

4. After 5 minutes, **Outbound Endpoint** will be configured in your VPC.


![RDGW](/images/5.1-CreateOE/0005.png?featherlight=false&width=90pc)

5. Once the **Outbound Endpoints** are created, click on the **Outbound Endpoint** to view the details of the endpoint. You will see the IP addresses assigned to the **Outbound Endpoints**. AWS injects an **elastic network interface** (ENI) into your subnet and assigns this IP address to the ENI.

![RDGW](/images/5.1-CreateOE/0006.png?featherlight=false&width=90pc)