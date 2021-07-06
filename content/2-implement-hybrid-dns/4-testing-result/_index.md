+++
title = "Kiểm tra kết quả"
date = 2021
weight = 4
chapter = false
pre = "<b>2.4. </b>"
+++

1. Kết nối vào **RD Gateway Server** (hoặc sử dụng phiên đã mở ở **phần 1.2**).
2. Mở **PowerShell** trên Windows và thực thi lệnh: ```Resolve-DnsName onprem.example.com```
3. Hoặc sử dụng **Command Prompt** và thực thi lệnh: ```nslookup onprem.example.com```

![2.4_CMD](../../../images/2/2.4_Result.png?width=90pc)

Bạn sẽ nhận được phản hồi DNS với địa chỉ IP chính xác cho Active Directory domain của mình.