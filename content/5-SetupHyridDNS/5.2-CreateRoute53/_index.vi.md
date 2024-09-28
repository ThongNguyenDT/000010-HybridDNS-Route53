---
title : "Tạo Route 53 Resolver Rules"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 5.2 </b> "
---

#### Tạo Route 53 Resolver Rules

Bước tiếp theo là tạo các **Route 53 Resolver** Rule. **Route 53 Resolver** rule cho phép xác định hai hành động: Forward hoặc System.

- Với Forward, bạn có thể cấu hình cho **Route 53 Resolver** chuyển tiếp các truy vấn **DNS** đến một **DNS** resolver bên ngoài (ví dụ: máy chủ **DNS** on-premise của bạn).
- Với System, Route 53 sẽ truy vấn nội bộ để phân giải tên miền (Private **DNS** zones, VPC **DNS**, và Public **DNS**).

1. Truy cập **Route 53 console** thông qua khung tìm kiếm và tìm **Route 53**.
   - Ở thanh bên trái, chọn **Rules** và chọn **Create rule**.

![RDGW](/images/5.2-CreateRoute53rule/0001.png?featherlight=false&width=90pc)

2. Nhập các thông tin sau:
   - **Name**: `FowardToOnPremAD`
   - **Rule type**: Forward
   - **Domain name**: `onprem.example.com.` (Đây là tên miền của directory mà bạn đã tạo ở phần trước)
   - **VPC that use this rule**: HybridDNS-VPCStack
   - **Outbound Endpoint**: R53-OutboundEndpoint

![RDGW](/images/5.2-CreateRoute53rule/0002.png?featherlight=false&width=90pc)

3. Ở Target IP addresses, nhập hai địa chỉ IP của **AWS Managed Microsoft Active Directory** đã được ghi nhận lại. Lưu ý, bạn cần phải chọn Add target để thêm địa chỉ IP thứ hai.

   - Chọn **Submit**

![RDGW](/images/5.2-CreateRoute53rule/0003.png?featherlight=false&width=90pc)

4. Hoàn thành tạo Route 53 Resolver

![RDGW](/images/5.2-CreateRoute53rule/0004.png?featherlight=false&width=90pc)

5. Tới đây, bạn đã cấu hình **Route 53 Resolver** để chuyển tiếp các truy vấn cho onprem.example.com tới một **DNS** resolver khác (ví dụ: AWS Managed Microsoft AD). Tên miền, onprem.example.com, mô phỏng tên miền **DNS** được host bởi hệ thống **DNS** on-premise của bạn.

![RDGW](/images/5.2-CreateRoute53rule/0005.png?featherlight=false&width=90pc)
