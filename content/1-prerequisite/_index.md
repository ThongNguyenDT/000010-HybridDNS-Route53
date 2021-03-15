+++
title = "Prerequiste"
date = 2020
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

The first step to building a Windows infrastructure in AWS is to build out the network infrastructure. In this section, you will leverage an AWS Quick Start to build out a secure highly available network infrastructure show below.

AWS Quick Starts leverage AWS CloudFormation which is AWS’s Infrastructure as Code (IaC) service that allows you to create infrastructure based upon a template (written in YAML or JSON). The template is uploaded to the CloudFormation service and itc creates the infrastructure described in the template.

#### Contents
- [1.1. Build Network with CloudFormation](./1-build-network-cf/)
- [1.2. Connecting to the Remote Desktop Gateway Server](./2-connect-to-rdgw/)
- [1.3. Deploy AWS Managed Microsoft Active Directory](./3-deploy-mad/)
