+++
title = "Xây dựng hạ tầng với CloudFormation"
date = 2020
weight = 1
chapter = false
pre = "<b>1.1. </b>"
+++

Bước đầu tiên bạn sẽ xây dựng cơ sở hạ tầng mạng trong AWS. Trong phần này, bạn sẽ tận dụng [**AWS Quick Start**](https://aws.amazon.com/quickstart/architecture/rd-gateway/) để xây dựng một hạ tầng mạng có tính sẵn sàng cao (HA) và bảo mật.

AWS Quick Starts sử dụng AWS CloudFormation là dịch vụ Infrastructure as Code (IaC) của AWS cho phép bạn tạo hạ tầng dựa trên template (được viết bằng YAML hoặc JSON). Template được tải lên dịch vụ CloudFormation và tự động tạo cơ sở hạ tầng được mô tả trong template.

![Overview Diagram](../../../images/1/0-diagram.png?width=40pc)

**Nội dung:**
- [1.1.1. Tạo Key Pair](#111-tạo-key-pair)
- [1.1.2. Khởi chạy Template CloudFormation Quick Start](#112-khởi-chạy-template-cloudformation-quick-start)
- [1.1.3. Thiết lập bảo mật](#113-thiết-lập-bảo-mật)

#### 1.1.1. Tạo Key Pair
Để đảm bảo truy cập an toàn vào các EC2 instance, AWS sử dụng private/public key có dạng một cặp khóa. Với các Windows instance, key pair được sử dụng để lấy mật khẩu administrator qua Amazon EC2 console. Trong phần này, bạn sẽ tạo key pair.

1. Đăng nhập vào **AWS Console** và truy cập vào **EC2 Management console** thông qua khung tìm kiếm và tìm **"EC2"**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn Asia Pacfic (Tokyo))
3. Ở menu bên trái, chọn **Key Pairs**.
4. Chọn **Create key pair**.
5. Ở màn hình **Create Key pair**,
   - Ở **Name**, nhập "hybrid-dns". (hay tên nào mà bạn mong muốnmuốn)
   - Ở **File format**, chọn pem.
   - Chọn **Create key pair**.
![Create Key Pair](../../../images/1/1-keypair.png?width=90pc)
6. **Quan trọng**: Chúng ta tải từ AWS key private của key pair với tên file **hybrid-dns.pem**. Hãy đảm bảo bạn đã lưu file PEM và nhớ vị trí lưu. Bạn sẽ phải dùng nó để giải mã password của administrator. Chúng ta không thể tải lại file key này.

#### 1.1.2. Khởi chạy Template CloudFormation Quick Start 
In this section, you are going to get hands-on experience with AWS CloudFormation to build out the base network infrastructure.
Trong phần này, bạn sẽ có trải nghiệm thực tế với AWS CloudFormation để xây dựng hạ tầng mạng.

1. Đăng nhập vào **AWS Console** và truy cập vào **CloudFormation (CFN) console** thông qua khung tìm kiếm và tìm **CloudFormation**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn Asia Pacfic (Tokyo))
3. Chọn **Create stack** > **With new resources (standard)**
4. Ở màn hình **Create stack**, nhập nội dung bên dưới và chọn **Next**.
   - **Prepare Template**: Template is ready
   - **Template Source**: Amazon S3 URL
   - **Amazon S3 URL**:  
```
https://aws-quickstart.s3.amazonaws.com/quickstart-microsoft-rdgateway/templates/rdgw-master.template
```
Hoặc tải Template ở phía dưới:
{{%attachments style="orange" title="CloudFormation Template" pattern=".*(template)"/%}}

![Create Stack](../../../images/1/2-createstack.png?width=90pc)

5. Ở **Stack name**, nhập HybridDNS.
6. Ở **Availability Zones**, chọn ap-northeast-1a và ap-northeast-1c.
7. Ở **VPC CIDR**, Private Subnet 1 & 2 CIDR, và Public Subnet 1 & 2 CIDR, giữ các giá trị mặc định.
![Create Stack](../../../images/1/2-createstack2.png?width=90pc)

8. Ở **Allowed Remote Desktop Gateway External Access CIDR**, nhập 0.0.0.0/0. 
{{% notice warning %}}
Thiết lập này sẽ cho phép bất kỳ IP nào cũng có thể Remote vào cổng RDP. 
Đây không phải là cấu hình an toàn và nó không được khuyến nghị khi triển khai ở môi trường production. Chúng ta sẽ quay lại và siết chặt quyền truy cập sau khi CloudFormation stack đã được triển khai.
{{% /notice %}} 
9.  Trong **Key Pair Name**, chọn Key Pair đã tạo trước đó (hybrid-dns).  
10. Ở **Remote Desktop Gateway Instance Type**, giữ giá trị mặc định (t2.large).  
11. Ở **Number of RDGW Hosts**, giữ giá trị mặc định (1).  
{{% notice note %}}
Ở Diagram phía trên thể hiện hai RDGW host (một host mỗi Availablity Zone (AZ)).  
Với mục tiêu làm thực hành, chúng ta sẽ bắt đầu với một RDGW host để giảm thời gian CloudFormation chạy khởi tạo. Tuy nhiên, theo như diagram, bạn có thể thấy RDGW host được triển khai vào Autoscaling Group.
Sau khi CloudFormation stack triển khai hoàn thành, bạn có thể thử cấu hình AutoScaling group. AutoScaling group là dịch vụ chủ chốt cung cấp tính sẵn sàng và mở rộng cho ứng dụng của bạn.
{{% /notice %}}
12. Ở **Admin User Name**, giữ giá trị mặc định (StackAdmin).  
13. Ở **Admin Password**, thiết lập mật khẩu dễ nhớ cho bạn. 
{{% notice note %}}
Mật khẩu yêu cầu phải đủ độ phức tạp (tối thiểu 8 ký tự và bao gồm cả ký tự chữ, ký tự số và ký tự đặc biệt).
{{% /notice %}}
14. Ở **Domain DNS Name**, giữ giá trị mặc định (example.com).  
15. Ở các lựa chọn khác, giữ giá trị mặc định và chọn **Next**.
![Create Stack](../../../images/1/2-createstack3.png?width=90pc)
16. Ở **Configure Stack Options**, kiểm tra lại các lựa chọn. Chọn **Next**.
17. Ở màn hình **Review HybridDNS**, kiểm tra lại thiết lập. Chọn vào hai lựa checkbox và chọn **Create Stack**.
![Create Stack](../../../images/1/2-createstack4.png?width=90pc)

{{% notice info %}}
Template mất khoảng 15 phút để hoàn thành. Trong thời gian này, chúng ta sẽ xem xét những gì mà template CloudFormation sẽ tạo.
Sau khi hoàn thành khởi tạo stack, trạng thái stack sẽ thay đổi thành **CREATE_COMPLETE**.
{{% /notice %}}

![Create Stack](../../../images/1/2-createstack5.png?width=90pc)

#### 1.1.3. Thiết lập bảo mật
Chúng ta sẽ siết chặt quyền truy cập RDGW host.

1. Đăng nhập vào **AWS Console** và truy cập vào **EC2 Management console** thông qua khung tìm kiếm và tìm **"EC2"**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn Asia Pacfic (Tokyo))
3. Ở menu bên trái, chọn **Security Groups**.
4. Chọn vào checkbox của security group có phần mô tả là **“Enable RDP access from the Internet”**
5. Ở khu vực phía dưới màn hình, chọn tab **Inbound**.
6. Chọn **Edit**.
![Secure Environment](../../../images/1/3-secureenvironment.png?width=90pc)
7. Chọn vào **Delete** ở kế rule có nội dung **Port Range, 3391** để xóa rule
8. Chọn vào **Delete** ở kế rule có nội dung **Port Range, 443** để xóa rule
9. Ở **RDP rule** trong cột **Source**, chọn ở danh sách **“My IP”**
10. Ở **ICMP rule** trong cột **Source**, chọn ở danh sách **“My IP”**
11. Chọn **Save**
![Secure Environment](../../../images/1/3-secureenvironment2.png?width=90pc)

{{% notice note %}}
Khi bảo mật ứng dụng của mình, bạn cần đảm bảo chỉ mở các cổng mà ứng dụng của bạn cần.  
Trong ví dụ này, bạn đã xóa cổng 3391 và 443, vì bạn sẽ không sử dụng các cổng đó trong bài thực hành này. Ngoài ra, bạn đã khóa quyền truy cập để các kết nối RDP và ICMP chỉ có thể bắt nguồn từ địa chỉ IP public của bạn.  
Một số khách hàng khóa quyền truy cập nhằm hạn chế các kết nối RDP và ICMP chỉ có thể bắt nguồn từ các địa chỉ IP public của hệ thống mạng công ty của họ.
{{% /notice %}}