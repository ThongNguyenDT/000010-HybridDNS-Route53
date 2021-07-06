+++
title = "Thiết lập Hybrid DNS"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

#### Tổng quan

Trong phòng phần thực hành này, bạn sẽ sử dụng ba công cụ (Outbound Endpoint, Resolver Rules, và Inbound Endpoints) của Route 53 Resolver để thiết lập hybrid DNS cho hạ tầng AWS và On-premise.  

Dịch vụ **AWS Managed Microsoft Active Directory** mà bạn đã tạo ở phần trước sẽ được sử dụng để **mô phỏng hệ thống DNS** on-premise của bạn. Hình dưới đây sẽ thể hiện kiến trúc mà bạn sẽ xây dựng tiếp tục dựa trên những hạ tầng mà bạn đã triển khai ở phần trước:

![Overview Diagram](../../../images/2/Architecture-2_HybridDNS.png?width=60pc)

**Giải thích:**
1. **Mũi tên màu đỏ** -- Bạn sẽ cấu hình **Outbound Endpoint** để tạo cầu nối cho **Route 53 Resolver** có thể chuyển tiếp (*forward*) các truy vấn DNS tới **AWS Managed Active Directory**.
2. Bạn sẽ tạo **Route 53 Resolver Rule** để lập chỉ dẫn cho việc chuyển tiếp các truy vấn DNS từ **Route 53 Resolver**  ra bên ngoài tới **AWS Managed Active Directory**.
3. **Mũi tên màu xanh dương** -- Bạn sẽ cấu hình **Inbound Endpoint** để tạo cầu nối cho **AWS Managed Active Directory** có thể chuyển tiếp các truy vấn DNS tới **Route 53 Resolver**. Từ đó, **Route 53 Resolver** có thể chuyến tiếp các truy vấn ấy tới các EC2 instance đang đóng vai trò là Remote Desktop Gateway.
4. **Mũi tên màu xanh lá** -- EC2 instance sẽ kết nối tới **Route 53 Resolver** bằng địa chỉ IP VPC+2. Theo mặc định, VPC+2 là địa chỉ IP cho DNS Resolver của VPC. (Ví dụ: VPC CIDR ở bài này là 10.0.0.0/16. Vậy, địa chỉ IP của DNS Resolver trong VPC là 10.0.0.2). 
5. **Mũi tên màu đen** -- **Route 53 Resolver** có thể chuyển tiếp các truy vấn DNS từ EC2 instance hoặc **AWS Managed Active Directory** tới các dịch vụ khác của AWS.


#### Nội dung
- [2.1. Cấu hình Route 53 Outbound Endpoint](./1-outbound-endpoint/)
- [2.2. Cấu hình  Route 53 Resolver Rules](./2-route53-rule/)
- [2.3. Cấu hình  Route 53 Inbound Endpoints](./3-inbound-endpoint/)
- [2.4. Thử nghiệm kết quả](./4-testing-result/)

{{% notice note %}}
Sau khi thực hiện, bạn sẽ hiểu được cách thiết lập hybrid DNS giữa các DNS hosted zone ở hệ thống on-premise và ở AWS. Trong bài thực hành, chúng ta đã sử dụng máy chủ AWS Managed Microsoft AD DNS để mô phỏng hệ thống DNS on-premise. Để hình dung về sự tích hợp với môi trường on-premise thực tế của mình, bạn cần chỉ định địa chỉ IP cho các máy chủ DNS on-premise của mình thay vì địa chỉ IP của AWS Managed Microsoft AD DNS.  
Để cho phép các máy chủ DNS on-premise của bạn phân giải bất kì AWS Private Zones nào host trên Route 53, bạn sẽ tạo các DNS forwarding rule trong hệ thống DNS on-premise của mình. Đối với các tên miền DNS được host trên Route 53, hãy forward đến địa chỉ IP của Inbound Endpoint.
{{% /notice %}}
