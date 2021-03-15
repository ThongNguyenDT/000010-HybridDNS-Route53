+++
title = "Tạo Inbound Endpoint"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3. </b>"
+++

Để kích hoạt hệ thống DNS on-premise của bạn có thể truy vấn Route 53 Resolver cho bất kỳ DNS zones nào (e.g. Private Zones) được host trên Route 53, bạn cần tạo Route 53 Inbound endpoint. Inbound endpoint cho phép các dịch vụ khác truy vấn Route 53 để phân giải tên miền. Khi bạn tạo Inbound Endpoint, AWS sẽ tạo một elastic network interface (ENI) trong mỗi availability zone (AZ) mà bạn chỉ định sẽ nhận các truy vấn DNS đi vào.

![Overview Diagram](../../../images/2/0-diagram2.png?width=40pc)

**Nội dung:**
- [Tạo Inbound Endpoint](#tạo-inbound-endpoint)

#### Tạo Inbound Endpoint

1. Từ **Route 53 console**, chọn **Inbound endpoints** nằm trong **Resolver**.
2. Chọn **Create inbound endpoint**.
   - Ở **Endpoint name**: R53-InboundEndpoint
   - Ở **VPC in the Region**: HybridDNS-VPCStack
   - Ở **Security group for this endpoint**, chọn security group mà chúng ta tạo để bảo vệ Managed AD (**d-###….#_controllers**).
   {{% notice note %}}
   Thông tin ID ở môi trường thực hành của bạn sẽ khác với ví dụ đưa ra.
   {{% /notice %}}
![Inbound Endpoint](../../../images/2/3-inbound.png?width=90pc)
3. Ở IP address #1,
   - Ở **Availability Zone**, chọn "ap-northeast-1a"
   - Ở **Subnet**, chọn "Private subnet 1A"
   - Ở **IP address**, chọn "Use an IP address that is selected automatically"
4. Ở IP address #2,
   - Ở **Availability Zone**, chọn "ap-northeast-1c"
   - Ở **Subnet**, chọn "Private subnet 2A"
   - Ở **IP address**, chọn "Use an IP address that is selected automatically"
![Inbound Endpoint](../../../images/2/3-inbound2.png?width=90pc)
5.  Chọn **Submit**.
![Inbound Endpoint](../../../images/2/3-inbound3.png?width=90pc)

Khi các Inbound Endpoint được tạo, hãy nhấp vào inbound endpoint để xem thông tin chi tiết của endpoint. Bạn sẽ thấy các địa chỉ IP đã được gán cho các inbound endpoint. AWS đưa một elastic network interface (ENI) vào subnet của bạn và gán địa chỉ IP này cho ENI.