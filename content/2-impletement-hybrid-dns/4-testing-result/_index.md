+++
title = "Testing Result"
date = 2020
weight = 4
chapter = false
pre = "<b>2.4. </b>"
+++

**Contents:**
- [Testing Result](#testing-result)

#### Testing Result

1. Connect to your **RD Gateway Server** (or use an open session from **Prerequiste**).
2. Open **PowerShell** window and run the command: ```Resolve-DnsName onprem.example.com```
3. Or using **Command Prompt** and use: ```nslookup onprem.example.com```

![Test Resolver](../../../images/2/4-test.png?width=90pc)

![Test Resolver](../../../images/2/4-test2.png?width=90pc)

You should receive the DNS response with correct IP addresses for your Active Directory domain.