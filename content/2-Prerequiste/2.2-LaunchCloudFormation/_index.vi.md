---
title : "Khởi tạo CloudFormation Template"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

#### Khởi tạo CloudFormation Template

Ở bước này, bạn sẽ xây dựng cơ sở hạ tầng mạng trong AWS. Trong phần này, bạn sẽ tận dụng template từ **AWS Quick Start** để xây dựng một hạ tầng mạng có tính sẵn sàng cao (HA) và bảo mật bằng **AWS CloudFormation**. Đây là kiến trúc sẽ được xây dựng từ template.

![Launch CloudFormation](/images/2-Pre/0002.png?featherlight=false&width=45pc)

Trong phần này, bạn sẽ có trải nghiệm thực tế với **AWS CloudFormation** để xây dựng hạ tầng mạng.

1. Đăng nhập vào **AWS Management Console**


    - Tìm **CloudFormation**
    - Chọn **CloudFormation**

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0001.png?featherlight=false&width=90pc)

2. Trong giao diện **CloudFormation** chọn **Create stack**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0002.png?featherlight=false&width=90pc)

3. Trong giao diện **Create stack**

   - **Prepare Template**: Template is ready
   - **Template Source**: **Amazon S3 URL**
   - **Amazon S3 URL**: https://aws-quickstart.s3.amazonaws.com/quickstart-microsoft-rdgateway/templates/rdgw-master.template
   - Chọn **Next**

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0003.png?featherlight=false&width=90pc)

4. Thực hiện cấu hình stack

   - Ở Stack name, nhập **HybridDNS**.
   - Ở **Availability Zones**, chọn **ap-northeast-1a và ap-northeast-1**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0004.png?featherlight=false&width=90pc)

5. Thực hiện cấu hình Network.

   - Ở **VPC CIDR, Private Subnet 1 & 2 CIDR, và Public Subnet 1 & 2 CIDR**, giữ các giá trị mặc định.
   - Ở **Allowed Remote Desktop Gateway External Access CIDR**, nhập **0.0.0.0/0**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0005.png?featherlight=false&width=90pc)

{{% notice warning %}}
Thiết lập này sẽ cho phép bất kỳ IP nào cũng có thể Remote vào cổng RDP của EC2 instance sắp được tạo. Đây không phải là cấu hình an toàn và nó không được khuyến nghị khi triển khai ở môi trường production. Chúng ta sẽ quay lại và siết chặt quyền truy cập sau khi CloudFormation đã hoàn tất triển khai template.
{{% /notice %}}


6. Trong bước **Amazon EC2 configuration**

   - Trong **Key Pair Name**, chọn Key Pair đã tạo trước đó (hybrid-**DNS**).
   - Ở **Remote Desktop Gateway Instance Type**, giữ giá trị mặc định (t2.large).
   - Ở **Number of RDGW Hosts**, giữ giá trị mặc định (1).
   - Ở **Admin User Name**, giữ giá trị mặc định (StackAdmin).
   - **Admin Password**, thiết lập mật khẩu dễ nhớ cho bạn.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0006.png?featherlight=false&width=90pc)

{{% notice note %}}
Ở Diagram phía trên thể hiện hai RDGW host (một host mỗi Availablity Zone (AZ)).
Với mục tiêu làm thực hành, chúng ta sẽ bắt đầu với một RDGW host để giảm thời gian CloudFormation chạy khởi tạo. Tuy nhiên, theo như diagram, bạn có thể thấy RDGW host được triển khai vào Autoscaling Group. Sau khi CloudFormation stack triển khai hoàn thành, bạn có thể thử cấu hình AutoScaling group. AutoScaling group là dịch vụ chủ chốt cung cấp tính sẵn sàng và mở rộng cho ứng dụng của bạn.
{{% /notice %}}

7. Ở các lựa chọn khác, giữ giá trị mặc định và chọn Next

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0007.png?featherlight=false&width=90pc)

8. Chọn **Next**

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0008.png?featherlight=false&width=90pc)

9. Ở màn hình Review HybridDNS, kiểm tra lại thiết lập. Chọn vào hai lựa checkbox và chọn **Create Stack**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0009.png?featherlight=false&width=90pc)

10. Template mất khoảng 15 phút để hoàn thành. Trong thời gian này, chúng ta sẽ xem xét những gì mà template CloudFormation sẽ tạo. Sau khi hoàn thành khởi tạo stack, trạng thái stack sẽ thay đổi thành **CREATE_COMPLETE**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/00010.png?featherlight=false&width=90pc)

11. Xem **Output** của Stack vừa tạo.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/00011.png?featherlight=false&width=90pc)


