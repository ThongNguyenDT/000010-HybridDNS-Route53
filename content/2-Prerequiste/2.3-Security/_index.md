---
title : "Configuring Security Group"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

#### Configure Security Group

1. Log in to **AWS Console** and access the **EC2 Management Console**:
   - Open the AWS Console and search for "EC2" using the search box.
   - Ensure that you have chosen the correct Region. Look in the upper left corner of the AWS Console and select the desired Region (In this case, we are selecting ap-southeast-1).

   ![Security Group](/images/2.3-SecurityGroup/0001.png?width=90pc)

2. Within the **EC2** interface:
   - From the left-hand menu, click on **Security Groups**.
   - Check the checkbox next to the security group with the description "**Enable RDP access from the Internet**".
   - At the bottom of the screen, go to the Inbound tab.
   - Click on **Edit inbound rules**.

   ![Security Group](/images/2.3-SecurityGroup/0002.png?width=90pc)

3. Edit the **Inbound** configuration:
   - Click **Delete** next to the rule that specifies **Port Range** 3391 to remove the rule.
   - Click **Delete** next to the rule that specifies **Port Range** 443 to remove the rule.
   - For the RDP rule in the Source column, choose "**My IP**" from the list (for the lab, you can use **0.0.0.0/0**).
   - For the ICMP rule in the Source column, choose "**My IP**" from the list (for the lab, you can use **0.0.0.0/0**).
   - Click **Save rules**.

   ![Security Group](/images/2.3-SecurityGroup/0003.png?width=90pc)

4. Finish configuring the security group.

   ![Security Group](/images/2.3-SecurityGroup/0004.png?width=90pc)

{{% notice tip %}}
When securing your application, it's important to ***open only the ports that your application requires***. In this step, you have **removed ports *3391* and *443*** since they are not needed for this exercise. Additionally, you've restricted access so that RDP and ICMP connections are **allowed only from *your public IP*** address.
{{% /notice %}}