+++
title = "AWS Quick Start"
date = 2021
weight = 2
chapter = false
pre = "<b>1.1.2 </b>"
+++

![Overview Diagram](/images/1/Architecture-1.1_CFN.png?width=40pc)

####  Khởi chạy Template CloudFormation Quick Start 

Trong phần này, bạn sẽ có trải nghiệm thực tế với AWS CloudFormation để xây dựng hạ tầng mạng.

1. Đăng nhập vào **AWS Console** và truy cập vào **CloudFormation (CFN) console** thông qua khung tìm kiếm và tìm **CloudFormation**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn **ap-southeast-1**)
3. Chọn **Create stack** > **With new resources (standard)**
![1.1_CreateStack](/images/1/1.1_CreateStack.png?width=90pc)
4. Ở màn hình **Create stack**, nhập nội dung bên dưới và chọn **Next**.
   - **Prepare Template**: Template is ready
   - **Template Source**: Amazon S3 URL
   - **Amazon S3 URL**: [https://aws-quickstart.s3.amazonaws.com/quickstart-microsoft-rdgateway/templates/rdgw-master.template](https://aws-quickstart.s3.amazonaws.com/quickstart-microsoft-rdgateway/templates/rdgw-master.template)
   ![1.1_CreateStack1](/images/1/1.1_CreateStack1.png?width=90pc)

Hoặc tải Template ở phía dưới:
{{%attachments style="orange" title="CloudFormation Template" pattern=".*(template)"/%}}



1. Ở **Stack name**, nhập HybridDNS.
2. Ở **Availability Zones**, chọn ap-northeast-1a và ap-northeast-1c.
3. Ở **VPC CIDR**, Private Subnet 1 & 2 CIDR, và Public Subnet 1 & 2 CIDR, giữ các giá trị mặc định.
![1.1_CreateStack2](/images/1/1.1_CreateStack2.png?width=90pc)

1. Ở **Allowed Remote Desktop Gateway External Access CIDR**, nhập 0.0.0.0/0. 
{{% notice warning %}}
Thiết lập này sẽ cho phép bất kỳ IP nào cũng có thể Remote vào cổng RDP của EC2 instance sắp được tạo. Đây không phải là cấu hình an toàn và nó không được khuyến nghị khi triển khai ở môi trường production. Chúng ta sẽ quay lại và siết chặt quyền truy cập sau khi CloudFormation đã hoàn tất triển khai template.
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
14. Ở các lựa chọn khác, giữ giá trị mặc định và chọn **Next**.
![1.1_CreateStack3](/images/1/1.1_CreateStack3.png?width=90pc)
1.  Ở **Configure Stack Options**, giữ các lựa chọn mặc định. Chọn **Next**.
2.  Ở màn hình **Review HybridDNS**, kiểm tra lại thiết lập. Chọn vào hai lựa checkbox và chọn **Create Stack**.
![1.1_CreateStack4](/images/1/1.1_CreateStack4.png?width=90pc)

{{% notice info %}}
Template mất khoảng 15 phút để hoàn thành. Trong thời gian này, chúng ta sẽ xem xét những gì mà template CloudFormation sẽ tạo.
Sau khi hoàn thành khởi tạo stack, trạng thái stack sẽ thay đổi thành **CREATE_COMPLETE**.
{{% /notice %}}

![1.1_CreateStack5](/images/1/1.1_CreateStack5.png?width=90pc)
