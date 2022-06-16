---
title : "Thử nghiệm kết quả"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 5.4 </b> "
---

#### Thử nghiệm kết quả

1. Kết nối vào RD Gateway Server

- Sử dụng Command Prompt và thực thi lệnh: 

```
nslookup onprem.example.com
```

![Results](/images/5.4-Results/0001.png?featherlight=false&width=90pc)

2. Mở PowerShell trên **Windows** và thực thi lệnh: 

```
Resolve-DnsName onprem.example.com
```

![Results](/images/5.4-Results/0002.png?featherlight=false&width=90pc)