+++
title = "Config Inbound Endpoint"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

To enable your on-premises DNS infrastructure to query Route 53 Resolver for any DNS zones (e.g. Private Zones) hosted on Route 53, you need to create Route 53 Inbound endpoints. Inbound endpoints allows other services to query Route 53 for DNS resolution. When you create an Inbound Endpoint, AWS creates an elastic network interface (ENI) in each availability zone (AZ) that you specify that will receive the inbound DNS queries.

![Overview Diagram](../../../images/2/0-diagram2.png?width=40pc)

**Contents:**
- [Config Inbound Endpoint](#config-inbound-endpoint)

#### Config Inbound Endpoint

1. From the **Route 53 console**, select **Inbound endpoints** under **Resolver**.
2. Select **Create inbound endpoint**.
   - For **Endpoint name**: R53-InboundEndpoint
   - For **VPC in the Region**: HybridDNS-VPCStack
   - For **Security group for this endpoint**, choose the security group that we created to secure Managed AD (e.g. **d-###….#_controllers**).
   {{% notice note %}}
   The ids for your environment will be different than mine.
   {{% /notice %}}
![Inbound Endpoint](../../../images/2/3-inbound.png?width=90pc)
3. For IP address #1,
   - For **Availability Zone**, select us-east-1a
   - For **Subnet**, select Private subnet 1A
   - For **IP address**, Select Use an IP address that is selected automatically
4. For IP address #2,
   - For **Availability Zone**, select us-east-1b
   - For **Subnet**, select Private subnet 2A
   - For **IP address**, Select Use an IP address that is selected automatically
![Inbound Endpoint](../../../images/2/3-inbound2.png?width=90pc)
5.  Press **Submit**.
![Inbound Endpoint](../../../images/2/3-inbound3.png?width=90pc)

Once the Inbound endpoints are created, click on the inbound endpoint hyperlink for details on the endpoint. You should see the IP addresses that were assigned for the inbound endpoints. AWS put an elastic network interface (ENI) into your subnet and assigned this IP address to the ENI.