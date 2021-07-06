+++
title = "Kết nối đến RDGW"
date = 2020
weight = 2
chapter = false
pre = "<b>1.2. </b>"
+++

Tiếp theo, bạn sẽ đăng nhập vào instance Remote Desktop Gateway Server (RDGW) bằng Remote Desktop Protocol (RDP). Nếu bạn kết nối từ máy tính Windows, RDP sẽ có sẵn. Nếu bạn đang sử dụng máy Mac, vui lòng tải xuống ứng dụng RDP [tại đây](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac).

**Nội dung:**
- [Remote Desktop Gateway Server](#remote-desktop-gateway-server)

#### Remote Desktop Gateway Server


1. Đăng nhập vào **AWS Console** và truy cập vào **EC2 Management console**
2. Ở menu bên trái, chọn **Instances**.
3. Chọn checkbox ở vị trí máy chủ RDGW.
4. Chọn **Connect**. 
5. Chọn **RDP Client** và chọn **“Download Remote Desktop File”** để tải tập tin **RDP**.
6. Chọn **Get Password**.
7. Chọn **Browse** và trỏ đến vị trí tập tin key pair chúng ta đã tải trước đó.
![1.2_Connect](../../../images/1/1.2_Connect.png?width=90pc)
8. Chọn **Decrypt Password**.
9. Khi đã có mật khẩu được giải mã, sao chép và lưu lại.
10. Khởi chạy tập tin RDP đã tải và sử dụng mật khẩu ở trên để đăng nhập vào máy chủ RDGW.
![1.2_ConnectRDP](../../../images/1/1.2_ConnectRDP.png?width=90pc)
11. Đây là màn hình kết nối vào instance thành công:
![1.2_WindowScreen](../../../images/1/1.2_WindowScreen.png?width=90pc)
