---
title : "Kết nối đến RDGW"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

#### Kết nối đến RDGW

Tiếp theo, bạn sẽ đăng nhập vào instance **Remote Desktop Gateway Server (RDGW)** bằng **Remote Desktop Protocol (RDP)**. Nếu bạn kết nối từ máy tính **Windows**, RDP sẽ có sẵn. Nếu bạn đang sử dụng máy Mac, vui lòng tải xuống [ứng dụng RDP tại đây](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-mac).

1. Đăng nhập vào **AWS Console** và truy cập vào **EC2 Management console**

![RDGW](/images/3-RDGW/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **EC2**

    - Ở menu bên trái, chọn **Instances**.
    - Chọn checkbox ở vị trí máy chủ RDGW.
    - Chọn **Connect**.

![RDGW](/images/3-RDGW/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Connect to instance**


   - Chọn **RDP Client** và chọn “**Download Remote Desktop File**” để tải tập tin RDP.
   - Chọn **Get Password**.


![RDGW](/images/3-RDGW/0003.png?featherlight=false&width=90pc)

4. Trong giao diện **Get **Windows** password**

   - Chọn Browse và trỏ đến vị trí tập tin key pair chúng ta đã tải trước đó.
   - Chọn **Decrypt Password**.

![RDGW](/images/3-RDGW/0004.png?featherlight=false&width=90pc)

5. Khi đã có mật khẩu được giải mã, sao chép và lưu lại.

![RDGW](/images/3-RDGW/0005.png?featherlight=false&width=90pc)

6. Khởi chạy tập tin RDP đã tải và sử dụng mật khẩu ở trên để đăng nhập vào máy chủ RDGW.

   - Chọn **Connect**

![RDGW](/images/3-RDGW/0006.png?featherlight=false&width=90pc)

7. Nhập password và chọn **OK**

![RDGW](/images/3-RDGW/0007.png?featherlight=false&width=90pc)

8. Tiếp tục chọn **Yes**

![RDGW](/images/3-RDGW/0008.png?featherlight=false&width=90pc)

9. Đây là màn hình kết nối vào instance thành công

![RDGW](/images/3-RDGW/0009.png?featherlight=false&width=90pc)



