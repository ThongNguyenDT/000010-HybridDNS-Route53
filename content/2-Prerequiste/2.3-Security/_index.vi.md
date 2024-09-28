---
title : "Cấu hình Security Group"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

#### Cấu hình Security Group

1. Đăng nhập vào **AWS Console** và truy cập vào **EC2 Management console** thông qua khung tìm kiếm và tìm “EC2”.

   - Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của **AWS Console** và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn ap-southeast-1)

![Security Group](/images/2.3-SecurityGroup/0001.png?width=90pc)

2. Trong giao diện **EC2**

   - Ở menu bên trái, chọn **Security Groups**.
   - Chọn vào checkbox của security group có phần mô tả là “**Enable RDP access from the Internet**”
   - Ở khu vực phía dưới màn hình, chọn tab Inbound.
   - Chọn **Edit inbound rules**.

![Security Group](/images/2.3-SecurityGroup/0002.png?width=90pc)

3. Tiến hành cấu hình chỉnh sửa **Inbound**

   - Chọn vào **Delete** ở kế rule có nội dung **Port Range**, 3391 để xóa rule
   - Chọn vào **Delete** ở kế rule có nội dung **Port Range**, 443 để xóa rule
   - Ở RDP rule trong cột Source, chọn ở danh sách “**My IP**” (trong phạm vi bài lab có thể chọn **0.0.0.0/0**)
   - Ở ICMP rule trong cột Source, chọn ở danh sách “**My IP**” (trong phạm vi bài lab có thể chọn **0.0.0.0/0**)
   - Chọn Save rules

![Security Group](/images/2.3-SecurityGroup/0003.png?width=90pc)

4. Hoàn thành cấu hình security group.

![Security Group](/images/2.3-SecurityGroup/0004.png?width=90pc)

{{% notice tip %}}
Khi bảo mật ứng dụng của mình, bạn cần đảm bảo **chỉ mở các cổng mà ứng dụng của bạn cần**. Trong bước này, **bạn đã xóa cổng *3391* và *443***, vì bạn sẽ không sử dụng các cổng đó trong bài thực hành này. Ngoài ra, bạn đã khóa quyền truy cập để các kết nối RDP và ICMP **chỉ có thể bắt nguồn từ địa chỉ IP public của bạn**.
{{% /notice %}}