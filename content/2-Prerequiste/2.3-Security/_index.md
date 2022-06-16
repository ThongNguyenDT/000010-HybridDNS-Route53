---
title : "Configuring Security Group"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

#### Configure Security Group

1. Log in to **AWS Console** and access **EC2 Management console** through the search box and search for “EC2”.

   - Make sure you have selected the correct Region. Notice in the left corner of **AWS Console** and select the correct Region you need (Here we are selecting ap-southeast-1)


![Security Group](/images/2.3-SecurityGroup/0001.png?featherlight=false&width=90pc)

2. In the **EC2** interface

   - In the left menu, select **Security Groups**.
   - Select the checkbox of the security group whose description is “**Enable RDP access from the Internet**”
   - In the area at the bottom of the screen, select the Inbound tab.
   - Select **Edit inbound rules**.

![Security Group](/images/2.3-SecurityGroup/0002.png?featherlight=false&width=90pc)

3. Conduct configuration editing **Inbound**

   - Select **Delete** next to the rule that says **Port Range**, 3391 to delete the rule
   - Select **Delete** next to the rule that says **Port Range**, 443 to delete the rule
   - In the RDP rule in the Source column, select in the list "**My IP**" (within the lab you can choose **0.0.0.0/0**)
   - In the ICMP rule in the Source column, select from the list "**My IP**" (in the scope of the lab, you can choose **0.0.0.0/0**)
   - Select Save rules

![Security Group](/images/2.3-SecurityGroup/0003.png?featherlight=false&width=90pc)

4. Complete the security group configuration.

![Security Group](/images/2.3-SecurityGroup/0004.png?featherlight=false&width=90pc)

{{% notice note %}}
When securing your application, you need to make sure to open only the ports that your application needs. In this step, you removed ports 3391 and 443, as you will not be using them in this exercise. Also, you've blocked access so that RDP and ICMP connections can only originate from your public IP address.
{{% /notice %}}