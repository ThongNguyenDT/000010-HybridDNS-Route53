+++
title = "Tạo Outbound Endpoint"
date = 2020
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

Bước đầu tiên, chúng ta sẽ tạo **Route 53 Outbound Endpoint** để cho phép **Route 53 Resolver** có thể chuyển tiếp các truy vấn DNS có tên miền được host bên ngoài Route 53. Khi bạn Route 53 Outbound Endpoint, AWS sẽ tạo một elastic network interface (ENI) trong mỗi Availability Zones (AZ) mà bạn chỉ định.

![Overview Diagram](../../../images/2/Architecture-2.1_OutboundEndpoint.png?width=60pc)

**Nội dung:**
- [Cấu hình Outbound Endpoint](#cấu-hình-outbound-endpoint)

#### Cấu hình Outbound Endpoint

1. Truy cập **Route 53 console** thông qua khung tìm kiếm và tìm **Route 53**.
2. Mở rộng thanh bên trái, chọn **Outbound endpoints** và chọn **Create outbound endpoint**.
![2.1_CreateOutbound](../../../images/2/2.1_CreateOutbound.png?width=90pc)
3. Ở trang **Create outbound endpoint**, nhập các thông tin sau:
   - **Endpoint name**: R53-OutboundEndpoint
   - **VPC in the Region**: HybridDNS-VPCStack-\*. *(Đây là VPC được tạo bởi CloudFormation ở phần trước)*
   - **Security group for this endpoint**: d-###….#_controllers. *(Đây là security group mà CloudFormation đã tạo để bảo vệ kết nối tới AWS Managed Microsoft Active Directory)*
   {{% notice note %}}
   Thông tin ID ở môi trường thực hành của bạn sẽ khác với ví dụ đưa ra.
   {{% /notice %}}

![2.1_GeneralSettings](../../../images/2/2.1_GeneralSettings.png?width=90pc)

4. Ở IP address #1:
   - Ở **Availability Zone**, chọn "ap-southeast-1a"
   - Ở **Subnet**, chọn "Private subnet 1A"
   - Ở **IP address**, chọn "Use an IP address that is selected automatically"
5. Ở IP address #2:
   - Ở **Availability Zone**, chọn "ap-southeast-1c"
   - Ở **Subnet**, chọn "Private subnet 2A"
   - Ở **IP address**, chọn "Use an IP address that is selected automatically"

![2.1_IPAddress](../../../images/2/2.1_IPAddress.png?width=90pc)

6. Cuối cùng, chọn **Submit**. Sau 5 phút, Outbound endpoint sẽ được hoàn tất cấu hình trong VPC của bạn. 

Khi các Outbound Endpoint được tạo, hãy nhấp vào Outbound Endpoint để xem thông tin chi tiết của endpoint. Bạn sẽ thấy các địa chỉ IP đã được gán cho các Outbound Endpoint. AWS đưa một elastic network interface (ENI) vào subnet của bạn và gán địa chỉ IP này cho ENI.
![2.1_Result](../../../images/2/2.1_Result.png?width=90pc)

