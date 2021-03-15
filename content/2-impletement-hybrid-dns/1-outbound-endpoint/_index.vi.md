+++
title = "Tạo Outbound Endpoint"
date = 2020
weight = 1
chapter = false
pre = "<b>2.1. </b>"
+++

Bước đầu tiên, chúng ta sẽ tạo **Route 53 Outbound Endpoint** cho phép **Route 53 Resolver** có thể **chuyển tiếp các truy vấn DNS** nhằm phân giải các tên miền được host bên ngoài Route 53. Khi bạn Route 53 Outbound Endpoint, AWS sẽ tạo một elastic network interface (ENI) trong mỗi Availability Zones (AZ) mà bạn chỉ định.

![Overview Diagram](../../../images/2/0-diagram1.png?width=40pc)

**Nội dung:**
- [Cấu hình Outbound Endpoint](#cấu-hình-outbound-endpoint)

#### Cấu hình Outbound Endpoint

1. Đăng nhập vào **AWS Console** và truy cập vào **Directory Service console** thông qua khung tìm kiếm và tìm **Directory Services**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn Asia Pacfic (Tokyo))
3. Chọn vào **Directory ID** mà bạn đã triển khai ở phần trước.
4. Ghi chú lại địa chỉ IP DNS của directory. Khi bạn tạo Managed Active Directory, nó sẽ đi kèm dịch vụ DNS trên mỗi domain controller. Bạn sẽ cần phải chuyển tiếp các truy vấn DNS về tên miền của Active Directory đến đúng máy chủ DNS.
5. Truy cập **Route 53 console** thông qua khung tìm kiếm và tìm **Route 53**.
6. Ở trong mục **Resolver**, chọn **Outbound endpoints** và chọn **Create outbound endpoint**.
7. Nhập các thông tin sau:
   - **Endpoint name**: R53-OutboundEndpoint
   - **VPC in the Region**: ap-northeast-1 (Tokyo): HybridDNS-VPCStack-*
   - Ở **Security group for this endpoint**, chọn security group mà chúng ta tạo để bảo vệ Managed AD (**d-###….#_controllers**).
   {{% notice note %}}
   Thông tin ID ở môi trường thực hành của bạn sẽ khác với ví dụ đưa ra.
   {{% /notice %}}

![Outbound Endpoint](../../../images/2/1-outbound.png?width=90pc)

8. Ở IP address #1:
   - Ở **Availability Zone**, chọn "ap-northeast-1a"
   - Ở **Subnet**, chọn "Private subnet 1A"
   - Ở **IP address**, chọn "Use an IP address that is selected automatically"
9. Ở IP address #2:
   - Ở **Availability Zone**, chọn "ap-northeast-1c"
   - Ở **Subnet**, chọn "Private subnet 2A"
   - Ở **IP address**, chọn "Use an IP address that is selected automatically"

![Outbound Endpoint](../../../images/2/1-outbound2.png?width=90pc)

10. Cuối cùng, chọn **Submit**.
{{% notice tip %}}
Sau 5 phút, Outbound endpoint sẽ hoàn tất cấu hình trong VPC của bạn.
{{% /notice %}}

![Outbound Endpoint](../../../images/2/1-outbound3.png?width=90pc)
