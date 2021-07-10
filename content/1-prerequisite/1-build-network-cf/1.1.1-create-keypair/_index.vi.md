+++
title = "Tạo Key Pair"
date = 2021
weight = 1
chapter = false
pre = "<b>1.1.1 </b>"
+++


![Overview Diagram](/images/1/Architecture-1.1_CFN.png?width=40pc)


#### Tạo Key Pair
Để đảm bảo truy cập an toàn vào các EC2 instance, AWS sử dụng private/public key có dạng một cặp khóa. Với các Windows instance, key pair được sử dụng để lấy mật khẩu administrator qua Amazon EC2 console. Trong phần này, bạn sẽ tạo key pair.

{{% notice note %}}
Nếu bạn đã tạo một key pair từ trước, bạn có thể sử dụng key pair sẵn có của mình và bỏ qua bước này.
{{% /notice %}}

1. Đăng nhập vào **AWS Console** và truy cập vào **EC2 Management console** thông qua khung tìm kiếm và tìm **"EC2"**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn **ap-southeast-1**)
3. Ở menu bên trái, chọn **Key Pairs**.
![1.1_Region](/images/1/1.1_Region.png?width=90pc)
1. Chọn **Create key pair**.
2. Ở màn hình **Create Key pair**,
   - Ở **Name**, nhập "hybrid-dns". (hay tên nào mà bạn mong muốnmuốn)
   - Ở **File format**, chọn pem.
   - Chọn **Create key pair**.
![1.1_keypair](/images/1/1.1_keypair.png?width=90pc)

1. **Quan trọng**: AWS sẽ tự động tải file private của key pair với tên file **hybrid-dns.pem**. Hãy đảm bảo bạn đã lưu file PEM và nhớ vị trí lưu vì bạn không thể tải lại file key này. Bạn sẽ phải dùng nó để giải mã password và kết nối tới EC2 instance được triển khai ở bước tiếp theo. 
