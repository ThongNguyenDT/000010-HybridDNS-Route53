---
title : "Test results"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 5.4 </b> "
---

#### Test results

1. Connect to RD Gateway Server

- Use Command Prompt and execute the command:

```
nslookup onprem.example.com
```

![Results](/images/5.4-Results/0001.png?featherlight=false&width=90pc)

2. Open PowerShell on **Windows** and execute the command:

```
Resolve-DnsName onprem.example.com
```

![Results](/images/5.4-Results/0002.png?featherlight=false&width=90pc)