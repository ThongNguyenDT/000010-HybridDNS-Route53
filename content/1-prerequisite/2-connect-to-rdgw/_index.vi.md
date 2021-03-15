+++
title = "Kết nối đến RDGW"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2. </b>"
+++

**Nội dung:**
- [Remote Desktop Gateway Server](#remote-desktop-gateway-server)

#### Remote Desktop Gateway Server
Tiếp theo, bạn sẽ đăng nhập vào máy chủ Remote Desktop Gateway Server (RDGW) bằng Remote Desktop Protocol (RDP). Nếu bạn kết nối từ máy tính Windows, RDP sẽ có sẵn. Nếu bạn đang sử dụng máy Mac, vui lòng tải xuống ứng dụng RDP [tại đây](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac).

1. Đăng nhập vào **AWS Console** và truy cập vào **EC2 Management console**
2. Ở menu bên trái, chọn **Instances**.
3. Chọn checkbox ở vị trí máy chủ RDGW.
4. Chọn **Connect**. Chọn **“Download Remote Desktop File”** để tải tập tin **RDP**.
5. Chọn **Get Password**.
6. Chọn **Choose File** và trỏ đến vị trí tập tin key pair chúng ta đã tải trước đó.

![Remote to Gateway](../../../images/1/4-remotetordgw.png?width=90pc)

7. Chọn **Decrypt Password**.
8. Khi đã có mật khẩu được giải mã, sao chép và lưu lại.
9. Khởi chạy tập tin RDP đã tải và sử dụng mật khẩu ở trên để đăng nhập vào máy chủ RDGW.

![Remote to Gateway](../../../images/1/4-remotetordgw2.png?width=90pc)
