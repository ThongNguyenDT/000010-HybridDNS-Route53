---
title : "Generate Key Pair"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Generate Key Pair

To ensure secure access to **EC2 instances**, AWS uses a private/public key in the form of a key pair. With **Windows** instances, the key pair is used to obtain the administrator password via the **Amazon EC2 console**. In this section, you will create a key pair.

![Create Key Pair](/images/2-Pre/0003.png?featherlight=false&width=45pc)

1. Go to **AWS Management Console**

   - Find EC2
   - Select **EC2**

   ![Create Key Pair](/images/2.1-CreateKeypair/0001.png?featherlight=false&width=90pc)

2. In **EC2** interface

   - Select **Key Pairs**
   - Select **Create key pair**

   ![Create Key Pair](/images/2.1-CreateKeypair/0002.png?featherlight=false&width=90pc)

3. In the **Create key pair** interface

   - Enter **hyrid-DNS** for **Name**
   - **Key pair type**, select **RSA**
   - **Private key file format**, select **.pem**
   - Select **Create key pair**

   ![Create Key Pair](/images/2.1-CreateKeypair/0003.png?featherlight=false&width=90pc)

4. Generate key pair successfully.

   ![Create Key Pair](/images/2.1-CreateKeypair/0004.png?featherlight=false&width=90pc)

5. **Important:** AWS will automatically download the private key pair file with the filename **hybrid-DNS.pem**. Make sure you have saved the PEM file and remember the save location because you cannot reload this key file. You will have to use it to decrypt the password and connect to the **EC2 instance** deployed in the next step.
