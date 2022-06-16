---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Clean up resources

#### Remove inbound endpoint

- Access to Route 53 Management Console
- In the left sidebar, select Inbound endpoints
- Tick the Inbound endpoint related to the lab
- Select **Delete**
- Type **Delete** in the empty box and press Submit

#### Remove Resolver Rule

  - Access to Route 53 Management Console
  - In the left sidebar, select Rules
  - Click on the Rule related to the lab to enter the Rule information page
  - In the VPCs section, tick the VPC that is connected to the Rule and select Disassociate
  - Type disassociate in the box and select Submit
  - Wait 1-2 minutes to disconnect from that VPC.
  - In the information page of the Rule, select **Delete**
  - Type **Delete** in the empty box and press Submit

#### Delete **Outbound Endpoint**

  - Access to Route 53 Management Console
  - In the left sidebar, select Outbound Endpoint**s**
  - Tick **Outbound Endpoint** related to the lab
  - Select **Delete**
  - Type **Delete** in the empty box and press Submit

#### Remove AWS Managed Microsoft Active Directory

  - Access to Directory Service Management Console
  - In the left sidebar, select Directories
  - Tick on the Directory related to the lab
  - Select Actions and select **Delete** directory
  - Type the domain name **DNS** of the directory in the empty box and press **Delete**

#### Delete CloudFormation Stack - when you delete CloudFormation Stack, the resources created by that stack are deleted.

  - In this case, the Hybrid**DNS** stack has created two nested stacks, and when you delete the Hybrid**DNS** stack, the two-child stacks are also deleted.
  - Access to CloudFormation Management Console
  - In the left sidebar, select Stacks
  - Tick the Hybrid**DNS** stack and select **Delete**
  - In the prompt, select **Delete** stack
  - Wait a few minutes until CloudFormation clears all resources