---
title : "Tạo Route 53 Outbound Endpoint"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 5.1 </b> "
---

#### Tạo Route 53 Outbound Endpoint

**Bước 1:** Đầu tiên, chúng ta sẽ tạo một **Outbound Endpoint** trong Route 53 để cho phép **Route 53 Resolver** chuyển tiếp các truy vấn **DNS** đối với tên miền được đặt trên hệ thống ngoài của Route 53. Khi bạn tạo một **Outbound Endpoint** trong Route 53, AWS sẽ tự động tạo một **Elastic Network Interface** (ENI) trong mỗi **Availability Zone** (AZ) mà bạn chỉ định.

![RDGW](/images/2-Pre/0006.png?featherlight=false&width=45pc)

**Bước 2:** Truy cập giao diện Route 53 thông qua khung tìm kiếm và chọn mục Route 53.
- Mở rộng menu bên trái, chọn **Outbound Endpoints** và nhấn vào **Create Outbound Endpoint**.

![RDGW](/images/5.1-CreateOE/0001.png?featherlight=false&width=90pc)

**Bước 3:** Tại trang **Create Outbound Endpoint**, điền các thông tin sau:
   - **Endpoint name**: `R53-OutboundEndpoint`
   - **VPC in the Region**: HybridDNS-VPCStack- (Đây là VPC đã được tạo bởi CloudFormation trong phần trước)
   - **Security group for this endpoint**: d-###….#_controllers (Đây là security group được tạo bởi CloudFormation để bảo vệ kết nối tới **AWS Managed Microsoft Active Directory**)

![RDGW](/images/5.1-CreateOE/0002.png?width=92pc)

**Bước 4:** Tiến hành cấu hình **IP addresses**

- **IP address #1:**
  - Ở **Availability Zone**, chọn “ap-southeast-1a”
  - Ở **Subnet**, chọn “Private subnet 1A”
  - Ở **IP address**, chọn “Use an IP address that is selected automatically”
- **IP address #2:**
  - Ở **Availability Zone**, chọn “ap-southeast-1c”
  - Ở **Subnet**, chọn “Private subnet 2A”
  - Ở **IP address**, chọn “Use an IP address that is selected automatically”

![RDGW](/images/5.1-CreateOE/0003.png?width=92pc)

**Bước 5:** Cuối cùng, nhấp vào **Create Outbound Endpoint**.

![RDGW](/images/5.1-CreateOE/0004.png?featherlight=false&width=90pc)

**Bước 6:** Sau khoảng 5 phút, **Outbound Endpoint** sẽ được cấu hình thành công trong VPC của bạn.

![RDGW](/images/5.1-CreateOE/0005.png?featherlight=false&width=90pc)

**Bước 7:** Khi các **Outbound Endpoint** đã được tạo, nhấp vào mục **Outbound Endpoint** để xem thông tin chi tiết. Bạn sẽ thấy danh sách các địa chỉ IP đã được gán cho các **Outbound Endpoint**. AWS sẽ đặt một **Elastic Network Interface** (ENI) trong subnet của bạn và gán địa chỉ IP này cho ENI.

![RDGW](/images/5.1-CreateOE/0006.png?featherlight=false&width=90pc)
