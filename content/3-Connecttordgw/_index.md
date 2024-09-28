---
title : "Connecting to RDGW"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Connect to RDGW

In this section, you will learn how to connect to the **Remote Desktop Gateway Server (RDGW)** instance using the **Remote Desktop Protocol (RDP)**. The process varies depending on your operating system.

1. **Login to AWS Console** and access the **EC2 Management console**.

    ![RDGW](/images/3-RDGW/0001.png?width=90pc)

2. In the **EC2** interface:

    - On the left menu, select **Instances**.
    - Check the checkbox next to the RDGW server instance.
    - Click on **Connect**.

    ![RDGW](/images/3-RDGW/0002.png?width=90pc)

3. In the **Connect to instance** interface:

    - Choose **RDP Client** and then select "**Download Remote Desktop File**" to download the RDP file.
    - Click on **Get Password**.

    ![RDGW](/images/3-RDGW/0003.png?width=90pc)

4. In the **Get Windows password** interface:

    - Click on **Browse** and navigate to the location where you saved the key pair file downloaded earlier.
    - Click on **Decrypt Password**.

    ![RDGW](/images/3-RDGW/0004.png?width=90pc)

5. Once you have the decrypted password, make sure to copy and save it securely.

    ![RDGW](/images/3-RDGW/0005.png?width=90pc)

6. Launch the downloaded RDP file and use the password obtained in the previous step to log in to the RDGW server.

    - Click on **Connect**.

    ![RDGW](/images/3-RDGW/0006.png?featherlight=false&width=90pc)

7. Enter the password and click on **OK**.

    ![RDGW](/images/3-RDGW/0007.png?featherlight=false&width=90pc)

8. Continue by selecting **Yes**.

    ![RDGW](/images/3-RDGW/0008.png?featherlight=false&width=90pc)

9. You should now see the screen indicating a successful connection to the instance.

    ![RDGW](/images/3-RDGW/0009.png?featherlight=false&width=90pc)
