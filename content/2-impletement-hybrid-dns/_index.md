+++
title = "Setting Up Hybrid DNS"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

In this lab, you will get hands-on experience with these three Route 53 resolver tools. **AWS Managed Microsoft Active Directory** will be used to **simulate your on-premises DNS** infrastructure.

![Overview Diagram](../../../images/2/0-diagram.png?width=40pc)

#### Contents
- [2.1. Configuring Route 53 Outbound Endpoint](./1-outbound-endpoint/)
- [2.2. Configuring Route 53 Resolver Rules](./2-route53-rule/)
- [2.3. Configuring Route 53 Inbound Endpoints](./3-inbound-endpoint/)
- [2.4. Testing Outbound Endpoint and Resolver Rule](./4-testing-result/)

After this lab, you learned how you can enable hybrid DNS name resolution between DNS zones hosted in your on-premises infrastructure and AWS. In the lab, we used AWS Managed Microsoft AD DNS servers to simulate your on-premises DNS infrastructure. If you wanted to envision the integration with your on-premises environment, you would specify the IP addresses for your on-premises DNS servers instead of the AWS Managed Microsoft AD DNS servers.

To enable your on-premises DNS servers to resolve any AWS Private Zones hosted on Route 53, you would create DNS forwarding rules in your on-premises DNS infrastructure. For the DNS domains hosted on Route 53, forward to the IP addresses of the Inbound Endpoints.
