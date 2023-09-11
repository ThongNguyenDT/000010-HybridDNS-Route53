---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Clean up resources

### Remove inbound endpoint

- Access to Route 53 Management Console
- In the left sidebar, select **Inbound endpoints**
- Tick the **Inbound endpoint** related to the lab
- Select **Delete**
- Type **Delete** in the empty box and press **Submit**

Explanation:
1. Open the Route 53 Management Console in your AWS account.
2. On the left sidebar, find and click on "Inbound endpoints."
3. Locate the specific **Inbound endpoint** associated with the lab.
4. Click on the **Delete** option.
5. A confirmation box will appear; enter **Delete** in the provided empty box and click **Submit**.

### Remove Resolver Rule

- Access to Route 53 Management Console
- In the left sidebar, select **Rules**
- Click on the **Rule** related to the lab to view its information
- In the VPCs section, select the connected VPC and choose **Disassociate**
- Type **disassociate** in the box and select **Submit**
- Wait 1-2 minutes for the disassociation process to complete.
- In the Rule information page, select **Delete**
- Type **Delete** in the empty box and press **Submit**

Explanation:
1. Access the Route 53 Management Console.
2. From the left sidebar, click on "Rules."
3. Locate and click on the specific **Rule** related to the lab to view its details.
4. Under the VPCs section, select the connected VPC and choose to **Disassociate**.
5. Type **disassociate** in the provided box and confirm with **Submit**.
6. Wait for 1-2 minutes to ensure disconnection from the VPC.
7. Return to the Rule information page, select **Delete**.
8. Confirm the deletion by typing **Delete** in the empty box and pressing **Submit**.

### Delete **Outbound Endpoint**

- Access to Route 53 Management Console
- In the left sidebar, select **Outbound Endpoints**
- Tick the **Outbound Endpoint** related to the lab
- Select **Delete**
- Type **Delete** in the empty box and press **Submit**

Explanation:
1. Open the Route 53 Management Console.
2. From the left sidebar, choose "Outbound Endpoints."
3. Locate and select the relevant **Outbound Endpoint** for the lab.
4. Click on **Delete**.
5. Confirm the deletion by entering **Delete** in the provided box and clicking **Submit**.

### Remove AWS Managed Microsoft Active Directory

- Access to Directory Service Management Console
- In the left sidebar, select **Directories**
- Tick the Directory related to the lab
- Select **Actions** and choose **Delete directory**
- Type the domain name (DNS) of the directory in the empty box and press **Delete**

Explanation:
1. Access the Directory Service Management Console.
2. From the left sidebar, click on "Directories."
3. Locate and select the relevant **Directory** associated with the lab.
4. Choose **Actions** and then select **Delete directory**.
5. Enter the domain name (DNS) of the directory in the provided box.
6. Confirm the deletion by clicking on **Delete**.

### Delete CloudFormation Stack

- Note: Deleting the CloudFormation Stack removes the resources created by it.

- In this case, the Hybrid**DNS** stack has created two nested stacks, and deleting the Hybrid**DNS** stack will also remove the child stacks.

- Access to CloudFormation Management Console
- In the left sidebar, select **Stacks**
- Tick the Hybrid**DNS** stack and select **Delete**
- In the prompt, choose **Delete stack**
- Wait for a few minutes while CloudFormation clears all resources

Explanation:
1. Note that deleting a CloudFormation Stack will result in the removal of the associated resources.
2. Specifically, in this scenario, the Hybrid**DNS** stack has generated two nested stacks, which will also be deleted upon removing the Hybrid**DNS** stack.
3. Access the CloudFormation Management Console.
4. From the left sidebar, click on "Stacks."
5. Locate and select the Hybrid**DNS** stack.
6. Choose **Delete** for stack removal.
7. Confirm the action by selecting **Delete stack** in the prompt.
8. Allow a few minutes for CloudFormation to complete the resource clearance.
