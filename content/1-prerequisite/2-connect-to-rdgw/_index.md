+++
title = "Connecting to RDGW"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2. </b>"
+++

**Contents:**
- [Remote Desktop Gateway Server](#remote-desktop-gateway-server)

#### Remote Desktop Gateway Server

You will next login to the Remote Desktop Gateway Server (RDGW) server using Remote Desktop Protocol (RDP). If you connecting from a Windows computer, RDP should be already present. If you are using a Mac, please download the RDP client [here](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac).

1. Log in to the **AWS Console** and go to **Elastic Compute Cloud (EC2) console**.
2. On the left hand menu, select **Instances**.
3. Select the checkbox near to the RDGW server.
4. Click the **Connect** button. Click the **“Download Remote Desktop File”** to download the **RDP file**.
5. Click the **Get Password** button.
6. Click the **Choose File** button and browse to the location of the key pair file that you downloaded earlier.

![Remote to Gateway](../../../images/1/4-remotetordgw.png?width=90pc)

7. Click **Decrypt Password**.
8. Once the password is decrypted, copy it to the clipboard.
9. Double click the RDP connection file that you downloaded and paste the password from the clipboard into the password field.

![Remote to Gateway](../../../images/1/4-remotetordgw2.png?width=90pc)
