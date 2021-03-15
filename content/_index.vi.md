+++
title = "Hybrid DNS với Route53 Resolver"
date = 2020
weight = 1
chapter = false
+++

# **Thiết lập Hybrid DNS với Route 53 Resolver**

Đa số các khách hàng hiện tại đang sở hữu một cơ sở hệ thống DNS on-premise. Khi bạn khởi tạo các tài nguyên trên nền tảng AWS, AWS có cung cấp dịch vụ DNS thông qua Amazon Route 53. Trong bài lab lần này, chúng ta sẽ tiến hành trải nghiệm bằng việc xây dựng hệ thống DNS hybrid nhằm cho phép bạn tích hợp với hệ thống DNS on-premise hiện tại với Amazon Route 53.

Route 53 cung cấp một số khả năng của DNS như: đăng ký miền DNS công cộng, khả năng tạo vùng DNS riêng, công cụ DNS hybrid và phân giải tên miền. Với tính năng phân giải tên miền, Route 53 Resolver có thể thực hiện tra cứu đệ quy đối với các hệ thống DNS công cộng.

Trong Route 53, dịch vụ Route 53 Resolver cung cấp ba công cụ để kích hoạt kiến trúc DNS hybrid giữa cơ sở hệ thống DNS on-premise của bạn và AWS. Ba công cụ này là:

* **Outbound Endpoints**: Các truy vấn DNS từ Route 53 Resolver đến hệ thống DNS on-premise của bạn sẽ được gửi đi từ Outbound Endpoints.
* **Inbound Endpoints**: Inbound endpoints đóng vai trò là mục tiêu cho các truy vấn DNS từ hệ thống DNS on-premise của bạn đến các tên miền được lưu trữ trên AWS.
* **Route 53 Resolver Rules**: Với Route 53 Resolver Rules, bạn có thể cấu hình Route 53 để chuyển tiếp các truy vấn DNS cho các tên miền cụ thể của bạn tới hệ thống DNS on-premise.
