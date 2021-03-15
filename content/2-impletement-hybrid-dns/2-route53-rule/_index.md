+++
title = "Config Route53 Resolver Rules"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

The next step is to create Route 53 Resolver Rules. Route 53 Resolver rules allow two actions: **Forward** or **System**. 
* With the **Forward** action, you can configure Route 53 resolver to **forward DNS queries** for specific DNS domain(s) to external DNS resolvers (e.g. your on-premises DNS servers).
* With **System**, Route 53 will **query its hierarchy** for name resolution (Private DNS zones, VPC DNS, and Public DNS).

**Contents:**
- [Config Route53 Resolver Rules](#config-route53-resolver-rules)

#### Config Route53 Resolver Rules

1. In the **Resolver** section, click **Rules** and then **Create a new rule**.
2. Enter the following information:
   - **Name**: FowardToOnPremAD
   - **Rule type**: Forward
   - **Domain name**: onprem.example.com
   ![Route 53 Resolver](../../../images/2/2-route53rule.png?width=90pc)
   - **VPC that use this rule**: HybridDNS-VPCStack
   - **Outbound endpoint**: R53-OutboundEndpoint
   - For the Target IP addresses, specify the **two IP addresses of your Managed AD domain controllers**, that you noted at the **Step 4 (Section 2.1)**. 
   {{% notice note %}}
   You will have to press **Add target** to add the second IP address.
   {{% /notice %}}
   ![Route 53 Resolver](../../../images/2/2-route53rule2.png?width=90pc)
   - Press **Submit**.
   ![Route 53 Resolver](../../../images/2/2-route53rule3.png?width=90pc)

Until now, you configured Route 53 Resolver to forward queries for **onprem.example.com** to another DNS resolver (e.g. AWS Managed Microsoft AD).  
The domain, onprem.example.com, simulates a DNS domain hosted by your on-premises DNS infrastructure.