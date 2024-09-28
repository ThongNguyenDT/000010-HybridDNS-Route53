---
title : "Khởi tạo CloudFormation Template"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

#### Khởi tạo CloudFormation Template

Trong bước này, bạn sẽ xây dựng cơ sở hạ tầng mạng trong AWS. Trong phần này, bạn sẽ tận dụng template từ **AWS Quick Start** để xây dựng một hạ tầng mạng có tính sẵn sàng cao (HA) và bảo mật bằng **AWS CloudFormation**. Dưới đây là kiến trúc sẽ được xây dựng từ template.

![Launch CloudFormation](/images/2-Pre/0002.png?width=45pc)

## Bước 1: Đăng nhập vào AWS Management Console

- Tìm và chọn **CloudFormation** trong AWS Management Console.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0001.png?width=90pc)

## Bước 2: Tạo stack CloudFormation

1. Trong giao diện **CloudFormation**, chọn **Create stack**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0002.png?width=90pc)

2. Trong giao diện **Create stack**:

   - **Prepare Template**: Template đã sẵn sàng.
   - **Template Source**: **Amazon S3 URL**
   - **Amazon S3 URL**: `https://aws-quickstart.s3.amazonaws.com/quickstart-microsoft-rdgateway/templates/rdgw-master.template`
   - Chọn **Next**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0003.png?width=90pc)

3. Thực hiện cấu hình stack:

   - Ở **Stack name**, nhập **HybridDNS**.
   - Ở **Availability Zones**, chọn **ap-northeast-1a và ap-northeast-1**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0004.png?width=90pc)

4. Thực hiện cấu hình Network:

   - Ở **VPC CIDR, Private Subnet 1 & 2 CIDR, và Public Subnet 1 & 2 CIDR**, giữ các giá trị mặc định.
   - Ở **Allowed Remote Desktop Gateway External Access CIDR**, nhập **`0.0.0.0/0`**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0005.png?width=70pc)

{{% notice warning %}}
Thiết lập này cho phép bất kỳ địa chỉ IP nào cũng có thể truy cập vào cổng RDP của EC2 instance sắp được tạo. Đây không phải là cấu hình an toàn và không nên được sử dụng trong môi trường production. Chúng ta sẽ điều chỉnh quyền truy cập sau khi quá trình triển khai template CloudFormation hoàn tất.
{{% /notice %}}

5. Trong bước **Amazon EC2 configuration**:

   - Trong **Key Pair Name**, chọn Key Pair đã tạo trước đó (**hybrid-DNS**).
   - Ở **Remote Desktop Gateway Instance Type**, giữ giá trị mặc định (t2.large).
   - Ở **Number of RDGW Hosts**, giữ giá trị mặc định (1).
   - Ở **Admin User Name**, giữ giá trị mặc định (StackAdmin).
   - **Admin Password**, thiết lập mật khẩu dễ nhớ cho bạn.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0006.png?width=70pc)

{{% notice tip %}}
Diagram trên hiển thị hai RDGW host (một host mỗi Availability Zone). Trong mục đích thực hành, chúng ta bắt đầu với một RDGW host để giảm thời gian khởi tạo của CloudFormation. Tuy nhiên, như trong diagram, bạn có thể thấy RDGW host được triển khai trong một Auto Scaling Group. Sau khi quá trình triển khai CloudFormation stack hoàn tất, bạn có thể thử cấu hình Auto Scaling group. Auto Scaling group là một dịch vụ quan trọng cung cấp tính sẵn sàng và mở rộng cho ứng dụng của bạn.
{{% /notice %}}

6. Ở các lựa chọn khác, giữ giá trị mặc định và chọn **Next**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0007.png?width=91pc)

7. Chọn **Next**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0008.png?width=90pc)

8. Kiểm tra lại thiết lập của stack trong màn hình Review HybridDNS. Chọn vào hai ô checkbox và chọn **Create Stack**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/0009.png?width=90pc)

9. Template mất khoảng 15 phút để hoàn thành. Trong thời gian này, chúng ta sẽ xem xét những thành phần mà template CloudFormation sẽ tạo. Sau khi quá trình khởi tạo stack hoàn tất, trạng thái của stack sẽ chuyển thành **CREATE_COMPLETE**.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/00010.png?width=90pc)

10. Xem phần **Output** của stack vừa được tạo.

![Launch CloudFormation](/images/2.2-LaunchCloudFormation/00011.png?width=91pc)


