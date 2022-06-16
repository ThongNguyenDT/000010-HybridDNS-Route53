---
title : "Connecting to RDGW"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Connect to RDGW

Next, you will log in to the **Remote Desktop Gateway Server (RDGW)** instance using **Remote Desktop Protocol (RDP)**. If you connect from a **Windows** computer, RDP will be available. If you are using a Mac, please download the [RDP client here](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac).

1. Login to **AWS Console** and access **EC2 Management console**

![RDGW](/images/3-RDGW/0001.png?featherlight=false&width=90pc)

2. In **EC2** interface

    - In the left menu, select **Instances**.
    - Select the checkbox at the RDGW server location.
    - Select **Connect**.

![RDGW](/images/3-RDGW/0002.png?featherlight=false&width=90pc)

3. In the **Connect to instance** interface


   - Select **RDP Client** and select “**Download Remote Desktop File**” to download the RDP file.
   - Select **Get Password**.


![RDGW](/images/3-RDGW/0003.png?featherlight=false&width=90pc)

4. In the **Get **Windows** password** interface

   - Select Browse and point to the location of the key pair file we downloaded earlier.
   - Select **Decrypt Password**.

![RDGW](/images/3-RDGW/0004.png?featherlight=false&width=90pc)

5. Once you have the decrypted password, copy and save it.

![RDGW](/images/3-RDGW/0005.png?featherlight=false&width=90pc)

6. Launch the downloaded RDP file and use the above password to login to the RDGW server.

   - Select **Connect**

![RDGW](/images/3-RDGW/0006.png?featherlight=false&width=90pc)

7. Enter the password and select **OK**

![RDGW](/images/3-RDGW/0007.png?featherlight=false&width=90pc)

8. Continue to select **Yes**

![RDGW](/images/3-RDGW/0008.png?featherlight=false&width=90pc)

9. This is the screen connecting to the instance successfully

![RDGW](/images/3-RDGW/0009.png?featherlight=false&width=90pc)