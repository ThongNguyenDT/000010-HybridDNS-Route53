+++
title = "Thử nghiệm kết quả"
date = 2020
weight = 4
chapter = false
pre = "<b>2.4. </b>"
+++

**Nội dung:**
- [Thử nghiệm kết quả](#thử-nghiệm-kết-quả)

#### Thử nghiệm kết quả

1. Kết nối vào **RD Gateway Server** (hoặc sử dụng phiên đã mở ở phần **Các bước chuẩn bị**).
2. Mở **PowerShell** trên Windows và thực thi lệnh: ```Resolve-DnsName onprem.example.com```
3. Hoặc sử dụng **Command Prompt** và thực thi lệnh: ```nslookup onprem.example.com```

![Test Resolver](../../../images/2/4-test.png?width=90pc)

![Test Resolver](../../../images/2/4-test2.png?width=90pc)

Bạn sẽ nhận được phản hồi DNS với địa chỉ IP chính xác cho Active Directory domain của mình.