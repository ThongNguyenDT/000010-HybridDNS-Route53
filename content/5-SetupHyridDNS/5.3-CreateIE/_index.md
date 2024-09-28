---
title : "Create Route 53 Inbound Endpoints"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
---

#### Create Route 53 Inbound Endpoints

To enable your on-premise **DNS** system to query **Route 53 Resolver** for specific **DNS** zones (such as Private Zones) hosted on Route 53, you need to set up a Route 53 Inbound Endpoint. This Inbound Endpoint serves as a link for other services to request domain name resolution from Route 53. When you create an Inbound Endpoint, AWS generates an elastic network interface (ENI) in each specified availability zone (AZ) to handle incoming **DNS** queries.

![Route 53 Inbound Endpoints](/images/2-Pre/0007.png?featherlight=true&width=45pc)

1. Access the Route 53 console:
   - Search for Route 53 in the search box.
   - Expand the left sidebar, go to **Inbound endpoints**, and select **Create inbound endpoint**.

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0001.png?featherlight=false&width=90pc)

2. On the *Create inbound endpoint* page, provide the following details:
   - **Endpoint name**: `R53-InboundEndpoint`
   - **VPC in the Region**: HybridDNS-VPCStack- (This VPC was created by CloudFormation in the previous section)
   - **Security group for this endpoint**: d-###….#_controllers (This security group was created by CloudFormation to secure the connection to AWS Managed Microsoft Active Directory)

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0002.png?width=90pc)

3. Configure **IP Addresses**:

- **IP address #1**:
  - **Availability Zone**: ap-northeast-1a
  - **Subnet**: Private subnet 1A
  - **IP address**: Use an automatically selected IP address
- **IP address #2**:
  - **Availability Zone**: ap-northeast-1c
  - **Subnet**: Private subnet 2A
  - **IP address**: Use an automatically selected IP address

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0003.png?width=90pc)

4. Click **Create inbound endpoint**.

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0004.png?featherlight=false&width=90pc)

5. Complete the creation of the **Inbound Endpoint**.

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0005.png?featherlight=false&width=90pc)

6. Once the Inbound Endpoints are successfully created, click on an inbound endpoint to view its details. You will find the IP addresses assigned to these inbound endpoints. AWS injects an elastic network interface (ENI) into your subnet and assigns the specified IP addresses to the ENIs.

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0006.png?featherlight=false&width=90pc)
