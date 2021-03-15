+++
title = "Config Outbound Endpoint"
date = 2020
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

The first step is to create **Route 53 Outbound Endpoints** which enable **Route 53 Resolver** to **forward DNS queries** to DNS domains hosted outside of Route 53. When you create Route 53 Outbound Endpoints, AWS will create an elastic network interface (ENI) in the Availability Zones (AZ) that you specify.

![Overview Diagram](../../../images/2/0-diagram1.png?width=40pc)

**Contents:**
- [Config Outbound Endpoint](#config-outbound-endpoint)

#### Config Outbound Endpoint

1. Login to the **AWS Console** and navigate to the Directory Service console. In the find a service search field, type Directory Services.
2. Make sure you are choosing the right region. Look at the upper right hand corner of the screen and switch to the your region if you are in a different region. (Here we use Asia Pacfic (Tokyo))
3. Click on **Directory ID** for the directory that you deployed in the previous Section.
4. Note the DNS addresses for your directory. When you created Managed Active Directory, it comes with DNS service on each domain controller. You need to enable forwarding DNS queries to your Active Directory domain to the right DNS servers.
5. Open **Route 53 console**. In the find a service search field, type **Route 53**.
6. In the **Resolver** section, click **Outbound endpoints** and then **Create outbound endpoint**.
7. Enter the following information:
   - **Endpoint name**: R53-OutboundEndpoint
   - **VPC in the Region**: ap-northeast-1 (Tokyo): HybridDNS-VPCStack-*
   - For the security group for this endpoint, select the security group that was created for the Managed AD setup earlier: “d-###..##_controllers …”. 
   {{% notice note %}}
   Your id for the Managed AD will be different from the one in my lab shown below.
   {{% /notice %}}

![Outbound Endpoint](../../../images/2/1-outbound.png?width=90pc)

8. IP address #1:
   -  **Availability Zone**: ap-northeast-1a
   -  **Subnet**: Private Subnet 1A
   -  **Use an IP address that is selected automatically**
9. IP address #2:
   -  **Availability Zone**: ap-northeast-1c
   -  **Subnet**: Private Subnet 2A
   -  **Use an IP address that is selected automatically**

![Outbound Endpoint](../../../images/2/1-outbound2.png?width=90pc)

10. Finally, click **Submit**.

{{% notice tip %}}
After 5 minutes, the Outbound endpoint will be configured in your VPC.
{{% /notice %}}

![Outbound Endpoint](../../../images/2/1-outbound3.png?width=90pc)
