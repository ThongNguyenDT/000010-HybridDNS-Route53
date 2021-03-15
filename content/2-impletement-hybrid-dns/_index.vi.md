+++
title = "Thiết lập Hybrid DNS"
date = 2020
weight = 2
chapter = false
pre = "<b>2. </b>"
+++

Trong phòng phần thực hành này, bạn sẽ sử dụng ba công cụ của Route 53 Resolver để thiết lập hybrid DNS cho hạ tầng AWS và On-premise.  
Dịch vụ **AWS Managed Microsoft Active Directory** sẽ được sử dụng để **mô phỏng hệ thống DNS** on-premise của bạn.

![Overview Diagram](../../../images/2/0-diagram.png?width=40pc)

#### Nội dung
- [2.1. Cấu hình Route 53 Outbound Endpoint](./1-outbound-endpoint/)
- [2.2. Cấu hình  Route 53 Resolver Rules](./2-route53-rule/)
- [2.3. Cấu hình  Route 53 Inbound Endpoints](./3-inbound-endpoint/)
- [2.4. Thử nghiệm kết quả](./4-testing-result/)

Sau khi thực hiện, bạn sẽ hiểu được cách thiết lập hybrid DNS giữa các DNS hosted zone ở hệ thống on-premise và ở AWS. Trong bài thực hành, chúng ta đã sử dụng máy chủ AWS Managed Microsoft AD DNS để mô phỏng hệ thống DNS on-premise. Để hình dung về sự tích hợp với môi trường on-premise thực tế của mình, bạn cần chỉ định địa chỉ IP cho các máy chủ DNS on-premise của mình thay vì địa chỉ IP của AWS Managed Microsoft AD DNS.

Để cho phép các máy chủ DNS on-premise của bạn phân giải bất kì AWS Private Zones nào host trên Route 53, bạn sẽ tạo các DNS forwarding rule trong hệ thống DNS on-premise của mình. Đối với các tên miền DNS được host trên Route 53, hãy forward đến địa chỉ IP của Inbound Endpoint.