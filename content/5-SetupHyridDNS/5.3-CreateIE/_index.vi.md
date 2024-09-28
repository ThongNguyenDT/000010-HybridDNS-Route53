---
title : "Tạo Route 53 Inbound Endpoints"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 5.3 </b> "
---

#### Tạo Route 53 Inbound Endpoints

Để cho phép hệ thống **DNS** on-premise của bạn có thể truy vấn **Route 53 Resolver** cho bất kỳ **DNS** zones nào (*ví dụ: Private Zones*) được host trên Route 53, bạn cần tạo Route 53 Inbound Endpoint. Inbound Endpoint là cầu nối cho các dịch vụ khác truy vấn Route 53 để phân giải tên miền. Khi bạn tạo Inbound Endpoint, AWS sẽ tạo một elastic network interface (ENI) trong mỗi availability zone (AZ) mà bạn chỉ định sẽ nhận các truy vấn **DNS** đi vào.

![Route 53 Inbound Endpoints](/images/2-Pre/0007.png?featherlight=true&width=45pc)

1. Truy cập Route 53 console thông qua khung tìm kiếm và tìm Route 53.
   - Mở rộng thanh bên trái, chọn **Inbound endpoints** và chọn **Create inbound endpoint**.

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0001.png?featherlight=false&width=90pc)

2. Ở trang Create inbound endpoint, nhập các thông tin sau:
   - Ở **Endpoint name**: `R53-InboundEndpoint`
   - **VPC in the Region**: HybridDNS-VPCStack-. (Đây là VPC được tạo bởi CloudFormation ở phần trước)
   - **Security group for this endpoint**: d-###….#_controllers. (Đây là security group mà CloudFormation đã tạo để bảo vệ kết nối tới AWS Managed Microsoft Active Directory)

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0002.png?width=90pc)

3. Cấu hình **IP Addresses**

- Ở **IP address #1:**
  - Ở **Availability Zone**, chọn "ap-northeast-1a"
  - Ở **Subnet**, chọn "Private subnet 1A"
  - Ở **IP address**, chọn "Use an IP address that is selected automatically"
- Ở **IP address #2:**
  - Ở **Availability Zone**, chọn "ap-northeast-1c"
  - Ở **Subnet**, chọn "Private subnet 2A"
  - Ở **IP address**, chọn "Use an IP address that is selected automatically"

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0003.png?width=90pc)

4. Chọn **Create inbound endpoint**

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0004.png?featherlight=false&width=90pc)

5. Hoàn thành tạo **Inbound Endpoint**

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0005.png?featherlight=false&width=90pc)

6. Khi các Inbound Endpoint được tạo, hãy nhấp vào inbound endpoint để xem thông tin chi tiết của endpoint. Bạn sẽ thấy các địa chỉ IP đã được gán cho các inbound endpoint. AWS đưa một elastic network interface (ENI) vào subnet của bạn và gán địa chỉ IP này cho ENI.

![Route 53 Inbound Endpoints](/images/5.3-CreateIE/0006.png?featherlight=false&width=90pc)

