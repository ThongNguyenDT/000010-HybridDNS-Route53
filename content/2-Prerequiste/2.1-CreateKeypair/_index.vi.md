---
title : "Tạo Key Pair"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

#### Tạo Key Pair

Để đảm bảo truy cập an toàn vào các **EC2 instance**, AWS sử dụng private/public key có dạng một cặp khóa. Với các **Windows** instance, key pair được sử dụng để lấy mật khẩu administrator qua **Amazon EC2 console**. Trong phần này, bạn sẽ tạo key pair.

![Create Key Pair](/images/2-Pre/0003.png?featherlight=false&width=45pc)


1. Truy cập vào **AWS Management Console**

- Tìm EC2
- Chọn **EC2**

![Create Key Pair](/images/2.1-CreateKeypair/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **EC2**

- Chọn **Key Pairs**
- Chọn **Create key pair**

![Create Key Pair](/images/2.1-CreateKeypair/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create key pair**

- Nhập **hyrid-DNS** cho **Name**
- **Key pair type**, chọn **RSA**
- **Private key file format**, chọn **.pem**
- Chọn **Create key pair**

![Create Key Pair](/images/2.1-CreateKeypair/0003.png?featherlight=false&width=90pc)

4. Tạo key pair thành công.

![Create Key Pair](/images/2.1-CreateKeypair/0004.png?featherlight=false&width=90pc)

5. Quan trọng: AWS sẽ tự động tải file private của key pair với tên file **hybrid-DNS.pem**. Hãy đảm bảo bạn đã lưu file PEM và nhớ vị trí lưu vì bạn không thể tải lại file key này. Bạn sẽ phải dùng nó để giải mã password và kết nối tới **EC2 instance** được triển khai ở bước tiếp theo.
