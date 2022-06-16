---
title : "Tạo Route 53 Outbound Endpoint"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

#### Tạo Route 53 **Outbound Endpoint**

Bước đầu tiên, chúng ta sẽ tạo Route 53 **Outbound Endpoint** để cho phép **Route 53 Resolver** có thể chuyển tiếp các truy vấn **DNS** có tên miền được host bên ngoài Route 53. Khi bạn Route 53 **Outbound Endpoint**, AWS sẽ tạo một **elastic network interface** (ENI) trong mỗi **Availability Zones** (AZ) mà bạn chỉ định.

![RDGW](/images/2-Pre/0006.png?featherlight=false&width=45pc)


1. Truy cập Route 53 console thông qua khung tìm kiếm và tìm Route 53.
- Mở rộng thanh bên trái, chọn Outbound Endpoint**s** và chọn Create **Outbound Endpoint**

![RDGW](/images/5.1-CreateOE/0001.png?featherlight=false&width=90pc)

2. Ở trang Create **Outbound Endpoint**, nhập các thông tin sau:
   - Endpoint name: R53-OutboundEndpoint
   - **VPC in the Region**: HybridDNS-VPCStack-. (Đây là VPC được tạo bởi CloudFormation ở phần trước)
   - **Security group for this endpoint**: d-###….#_controllers. (Đây là security group mà CloudFormation đã tạo để bảo vệ kết nối tới **AWS Managed Microsoft Active Directory**)

![RDGW](/images/5.1-CreateOE/0002.png?featherlight=false&width=90pc)

3. Thực hiện cấu hình **IP addresses**

- Ở **IP address #1:**
  - Ở **Availability Zone**, chọn “ap-southeast-1a”
  - Ở **Subnet**, chọn “Private subnet 1A”
  - Ở **IP address**, chọn “Use an IP address that is selected automatically”
- Ở **IP address #2:**
  - Ở **Availability Zone**, chọn “ap-southeast-1c”
  - Ở **Subnet**, chọn “Private subnet 2A”
  - Ở **IP address**, chọn “Use an IP address that is selected automatically”

![RDGW](/images/5.1-CreateOE/0003.png?featherlight=false&width=90pc)

3. Cuối cùng, chọn **Create Outbound Endpoint**.

![RDGW](/images/5.1-CreateOE/0004.png?featherlight=false&width=90pc)

4.  Sau 5 phút, **Outbound Endpoint** sẽ được hoàn tất cấu hình trong VPC của bạn.


![RDGW](/images/5.1-CreateOE/0005.png?featherlight=false&width=90pc)

5. Khi các **Outbound Endpoint** được tạo, hãy nhấp vào **Outbound Endpoint** để xem thông tin chi tiết của endpoint. Bạn sẽ thấy các địa chỉ IP đã được gán cho các **Outbound Endpoint**. AWS đưa một **elastic network interface** (ENI) vào subnet của bạn và gán địa chỉ IP này cho ENI.

![RDGW](/images/5.1-CreateOE/0006.png?featherlight=false&width=90pc)
