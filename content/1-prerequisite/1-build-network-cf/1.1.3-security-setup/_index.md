+++
title = "Thiết lập bảo mật"
date = 2021
weight = 3
chapter = false
pre = "<b>1.1.3 </b>"
+++


![Overview Diagram](../../../images/1/Architecture-1.1_CFN.png?width=40pc)


#### Thiết lập bảo mật
Trong bước này, chúng ta sẽ siết chặt quyền truy cập RDGW host.

1. Đăng nhập vào **AWS Console** và truy cập vào **EC2 Management console** thông qua khung tìm kiếm và tìm **"EC2"**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn **ap-southeast-1**)
3. Ở menu bên trái, chọn **Security Groups**.
4. Chọn vào checkbox của security group có phần mô tả là **“Enable RDP access from the Internet”**
5. Ở khu vực phía dưới màn hình, chọn tab **Inbound**.
6. Chọn **Edit inbound rules**.
![1.1_SG](../../../images/1/1.1_SG.png?width=90pc)
7. Chọn vào **Delete** ở kế rule có nội dung **Port Range, 3391** để xóa rule
8. Chọn vào **Delete** ở kế rule có nội dung **Port Range, 443** để xóa rule
9. Ở **RDP rule** trong cột **Source**, chọn ở danh sách **“My IP”**
10. Ở **ICMP rule** trong cột **Source**, chọn ở danh sách **“My IP”**
11. Chọn **Save rules**

{{% notice note %}}
Khi bảo mật ứng dụng của mình, bạn cần đảm bảo chỉ mở các cổng mà ứng dụng của bạn cần. Trong bước này, bạn đã xóa cổng 3391 và 443, vì bạn sẽ không sử dụng các cổng đó trong bài thực hành này. Ngoài ra, bạn đã khóa quyền truy cập để các kết nối RDP và ICMP chỉ có thể bắt nguồn từ địa chỉ IP public của bạn.
{{% /notice %}}