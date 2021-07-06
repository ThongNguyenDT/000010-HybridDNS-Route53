+++
title = "Tạo Inbound Endpoint"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

Để cho phép hệ thống DNS on-premise của bạn có thể truy vấn Route 53 Resolver cho bất kỳ DNS zones nào (e.g. Private Zones) được host trên Route 53, bạn cần tạo **Route 53 Inbound Endpoint**. Inbound Endpoint là cầu nối cho các dịch vụ khác truy vấn Route 53 để phân giải tên miền. Khi bạn tạo Inbound Endpoint, AWS sẽ tạo một elastic network interface (ENI) trong mỗi availability zone (AZ) mà bạn chỉ định sẽ nhận các truy vấn DNS đi vào.

![Architecture-2.3_InboundEndpoint](../../../images/2/Architecture-2.3_InboundEndpoint.png?width=40pc)

**Nội dung:**
- [Tạo Inbound Endpoint](#tạo-inbound-endpoint)

#### Tạo Inbound Endpoint
1. Truy cập **Route 53 console** thông qua khung tìm kiếm và tìm **Route 53**.
2. Mở rộng thanh bên trái, chọn **Inbound endpoints** và chọn **Create inbound endpoint**.
![2.3_CreateInbound](../../../images/2/2.3_CreateInbound.png?width=90pc)
3. Ở trang **Create inbound endpoint**, nhập các thông tin sau:
   - Ở **Endpoint name**: R53-InboundEndpoint
   - **VPC in the Region**: HybridDNS-VPCStack-\*. *(Đây là VPC được tạo bởi CloudFormation ở phần trước)*
   - **Security group for this endpoint**: d-###….#_controllers. *(Đây là security group mà CloudFormation đã tạo để bảo vệ kết nối tới AWS Managed Microsoft Active Directory)*
   {{% notice note %}}
   Thông tin ID ở môi trường thực hành của bạn sẽ khác với ví dụ đưa ra.
   {{% /notice %}}
![2.3_GeneralSettings](../../../images/2/2.3_GeneralSettings.png?width=90pc)
4. Ở IP address #1,
   - Ở **Availability Zone**, chọn "ap-northeast-1a"
   - Ở **Subnet**, chọn "Private subnet 1A"
   - Ở **IP address**, chọn "Use an IP address that is selected automatically"
5. Ở IP address #2,
   - Ở **Availability Zone**, chọn "ap-northeast-1c"
   - Ở **Subnet**, chọn "Private subnet 2A"
   - Ở **IP address**, chọn "Use an IP address that is selected automatically"
![2.3_IPAdress](../../../images/2/2.3_IPAddress.png?width=90pc)
6.  Chọn **Submit**. 

Khi các Inbound Endpoint được tạo, hãy nhấp vào inbound endpoint để xem thông tin chi tiết của endpoint. Bạn sẽ thấy các địa chỉ IP đã được gán cho các inbound endpoint. AWS đưa một elastic network interface (ENI) vào subnet của bạn và gán địa chỉ IP này cho ENI.
![2.3_Result](../../../images/2/2.3_Result.png?width=90pc)