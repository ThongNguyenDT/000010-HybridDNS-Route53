---
title : "Create Route 53 Inbound Endpoints"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
---

#### Create Route 53 Inbound Endpoints

To allow your **DNS** on-premise system to query **Route 53 Resolver** for any **DNS** zones (e.g. Private Zones) hosted on Route 53, you need to create Route 53 Inbound Endpoint. The Inbound Endpoint is a bridge for other services to query Route 53 for domain name resolution. When you create an Inbound Endpoint, AWS creates an elastic network interface (ENI) in each availability zone (AZ) that you specify that will receive inbound **DNS** queries.

![Route 53 Inbound Endpoints](/images/2-Pre/0007.png?featherlight=false&width=45pc)

1. Access Route 53 console through the search box and find Route 53.
   - Expand the left sidebar, select **Inbound endpoints** and select **Create inbound endpoint**.

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0001.png?featherlight=false&width=90pc)

2. On the Create inbound endpoint page, enter the following information:
   - At **Endpoint name**: R53-InboundEndpoint
   - **VPC in the Region**: HybridDNS-VPCStack-. (This is the VPC created by CloudFormation in the previous section)
   - **Security group for this endpoint**: d-###….#_controllers. (This is the security group that CloudFormation created to protect the connection to AWS Managed Microsoft Active Director)

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0002.png?featherlight=false&width=90pc)

3. Configure **IP Addresses**

- At **IP address #1:**
  - In **Availability Zone**, select “ap-northeast-1a”
  - In **Subnet**, select “Private subnet 1A”
  - In **IP address**, select “Use an IP address that is selected automatically”
- At **IP address #2:**
  - In **Availability Zone**, select “ap-northeast-1c”
  - In **Subnet**, select “Private subnet 2A”
  - In **IP address**, select “Use an IP address that is selected automatically”

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0003.png?featherlight=false&width=90pc)

4. Select **Create inbound endpoint**

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0004.png?featherlight=false&width=90pc)

5. Finish creating **Inbound Endpoint**

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0005.png?featherlight=false&width=90pc)

6. Once the Inbound Endpoints are created, click on the inbound endpoint to view the endpoint's details. You will see the IP addresses assigned to the inbound endpoints. AWS injects an elastic network interface (ENI) into your subnet and assigns this IP address to ENI.

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0006.png?featherlight=false&width=90pc)