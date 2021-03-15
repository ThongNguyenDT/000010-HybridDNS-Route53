+++
title = "Hybrid DNS with Route53 Resolver"
date = 2020
weight = 1
chapter = false
+++

# **Implement Hybrid DNS with Route53 Resolver**

Most customers have an on-premises DNS infrastructure. When you create resources in AWS, AWS provides DNS services provided by Amazon Route 53. In this lab, you will get hands-on experience with creating a hybrid DNS infrastructure which allows you to integrate your on-premises DNS infrastructure with Amazon Route 53 DNS.

Route 53 provides a number of DNS capabilities such as: public DNS domain registration, ability to create private DNS zones, hybrid DNS tools, and DNS name resolution. With DNS name resolution, Route 53 Resolver can perform recursive lookups against public name servers.

Within Route 53, the Route 53 Resolver service provides three tools to enable hybrid DNS architecture between your on-premises DNS infrastructure and AWS. These three tools are:

* **Outbound Endpoints**: DNS queries from Route 53 Resolver for your on-premises DNS infrastructure will originate from outbound endpoints.
* **Inbound Endpoints**: Inbound endpoints serve as targets for DNS queries from your on-premises DNS infrastructure for DNS domains hosted in AWS.
* **Route 53 Resolver Rules**: With Route 53 Resolver Rules, you can configure Route 53 to forward DNS queries for your specific DNS domains to on-premises DNS servers.
