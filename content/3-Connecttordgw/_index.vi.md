---
title : "Kết nối đến RDGW"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Kết nối đến RDGW

Bước tiếp theo là đăng nhập vào máy chủ **Remote Desktop Gateway (RDGW)** bằng giao thức **Remote Desktop Protocol (RDP)**. Nếu bạn đang sử dụng máy tính **Windows**, RDP đã có sẵn. Nếu bạn đang sử dụng máy Mac, bạn cần tải ứng dụng RDP tại [đây](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac).

1. Đăng nhập vào **AWS Console** và truy cập **EC2 Management Console**.

   ![RDGW](/images/3-RDGW/0001.png?width=90pc)

2. Trong giao diện **EC2**:

   - Trong menu bên trái, chọn **Instances**.
   - Chọn ô chọn ở máy chủ RDGW.
   - Chọn **Connect**.

   ![RDGW](/images/3-RDGW/0002.png?width=90pc)

3. Trong giao diện **Connect to Instance**:

   - Chọn **RDP Client** và chọn "Tải tập tin Remote Desktop".
   - Chọn **Get Password**.

   ![RDGW](/images/3-RDGW/0003.png?width=90pc)

4. Trong giao diện **Get Windows Password**:

   - Chọn **Browse** và tìm tập tin key pair bạn đã tải trước đó.
   - Chọn **Decrypt Password**.

   ![RDGW](/images/3-RDGW/0004.png?width=90pc)

5. Khi mật khẩu được giải mã, sao chép và lưu lại.

   ![RDGW](/images/3-RDGW/0005.png?width=90pc)

6. Mở tập tin RDP đã tải và sử dụng mật khẩu ở bước trước để đăng nhập vào máy chủ RDGW.

   - Chọn **Connect**.

   ![RDGW](/images/3-RDGW/0006.png?featherlight=false&width=90pc)

7. Nhập mật khẩu và chọn **OK**.

   ![RDGW](/images/3-RDGW/0007.png?featherlight=false&width=90pc)

8. Tiếp tục chọn **Yes**.

   ![RDGW](/images/3-RDGW/0008.png?featherlight=false&width=90pc)

9. Đây là màn hình kết nối thành công vào máy chủ.

   ![RDGW](/images/3-RDGW/0009.png?featherlight=false&width=90pc)




