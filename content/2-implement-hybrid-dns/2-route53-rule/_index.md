+++
title = "Tạo Route 53 Resolver Rule"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2. </b>"
+++

Bước tiếp theo là tạo các Route 53 Resolver Rule. Route 53 Resolver rule cho phép xác định hai hành động: **Forward** hoặc **System**.
* Với **Forward**, bạn có thể cấu hình cho Route 53 resolver **chuyển tiếp các truy vấn DNS** đến một DNS resolvers bên ngoài (ví dụ: máy chủ DNS on-premise của bạn).
* Với **System**, Route 53 sẽ **truy vấn nội bộ** để phân giải tên miền (Private DNS zones, VPC DNS, và Public DNS).

**Nội dung:**
- [Tạo Route 53 Resolver Rule](#tạo-route-53-resolver-rule)

#### Tạo Route 53 Resolver Rule
1. Truy cập **Route 53 console** thông qua khung tìm kiếm và tìm **Route 53**.
2. Ở thanh bên trái, chọn **Rules** và chọn **Create rule**.
![2.2_CreateRule](../../../images/2/2.2_CreateRule.png?width=90pc)
3. Nhập các thông tin sau:
   - **Name**: FowardToOnPremAD
   - **Rule type**: Forward
   - **Domain name**: onprem.example.com. *(Đây là tên miền của directory mà bạn đã tạo ở phần trước)*
   - **VPC that use this rule**: HybridDNS-VPCStack
   - **Outbound endpoint**: R53-OutboundEndpoint
   ![2.2_RuleForTraffic](../../../images/2/2.2_RuleForTraffic.png?width=90pc)
   - Ở **Target IP addresses**, nhập hai địa chỉ IP của AWS Managed Microsoft Active Directory đã được ghi nhận lại ở **Phần 1.3**. Lưu ý, bạn cần phải chọn **Add target** để thêm địa chỉ IP thứ hai.
4. Chọn **Submit**.
   ![2.2_Target](../../../images/2/2.2_Target.png?width=90pc)

Tới đây, bạn đã cấu hình Route 53 Resolver để chuyển tiếp các truy vấn cho **onprem.example.com** tới một DNS resolver khác (ví dụ: AWS Managed Microsoft AD).
Tên miền, onprem.example.com, mô phỏng tên miền DNS được host bởi hệ thống DNS on-premise của bạn.