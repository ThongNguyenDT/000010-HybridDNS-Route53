+++
title = "Tạo Route 53 Resolver Rule"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

Bước tiếp theo là tạo các Route 53 Resolver Rule. Route 53 Resolver rule cho phép xác định hai hành động: **Forward** hoặc **System**.
* Với **Forward**, bạn có thể cấu hình cho Route 53 resolver **chuyển tiếp các truy vấn DNS** với một tên miền cụ thể đến một DNS resolvers bên ngoài (ví dụ: máy chủ DNS on-premise của bạn).
* Với **System**, Route 53 sẽ **truy vấn nội bộ** để phân giải tên miền (Private DNS zones, VPC DNS, và Public DNS).

**Nội dung:**
- [Tạo Route 53 Resolver Rule](#tạo-route-53-resolver-rule)

#### Tạo Route 53 Resolver Rule

1. Ở trong mục **Resolver**, chọn **Rules** và chọn **Create a new rule**.
2. Nhập các thông tin sau:
   - **Name**: FowardToOnPremAD
   - **Rule type**: Forward
   - **Domain name**: onprem.example.com
   ![Route 53 Resolver](../../../images/2/2-route53rule.png?width=90pc)
   - **VPC that use this rule**: HybridDNS-VPCStack
   - **Outbound endpoint**: R53-OutboundEndpoint
   - Ở **Target IP addresses**, xác định cụ thể **hai địa chỉ IP của Managed AD domain controllers** đã được ghi nhận lại ở **Bước 4 (Phần 2.1)**. 
   {{% notice note %}}
   Bạn cần phải chọn **Add target** để thêm địa chỉ IP thứ hai.
   {{% /notice %}}
   ![Route 53 Resolver](../../../images/2/2-route53rule2.png?width=90pc)
   - Chọn **Submit**.
   ![Route 53 Resolver](../../../images/2/2-route53rule3.png?width=90pc)

Tới đây, bạn đã cấu hình Route 53 Resolver để chuyển tiếp các truy vấn cho **onprem.example.com** tới một DNS resolver khác (ví dụ: AWS Managed Microsoft AD).
Tên miền, onprem.example.com, mô phỏng tên miền DNS được host bởi hệ thống DNS on-premise của bạn.