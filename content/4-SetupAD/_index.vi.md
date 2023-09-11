---
title : "Triển khai Microsoft AD"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Triển khai Microsoft AD

Để giả lập **DNS** on-premise, chúng ta sẽ sử dụng dịch vụ **AWS Directory Service** để triển khai **AWS Managed Microsoft Active Directory** trong hai private subnet được tạo bởi CloudFormation như hình dưới đây:

![Hình ảnh](/images/2-Pre/0004.png?featherlight=false&width=45pc)

1. Đăng nhập vào **AWS Console** và truy cập vào Directory Service console thông qua khung tìm kiếm và tìm Directory Services.

   - Hãy chắc chắn bạn đã chọn đúng **Region** (vùng). Chú ý ở góc trái của **AWS Console** và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn ap-southeast-1)

   ![Hình ảnh](/images/4-AD/0001.png?featherlight=false&width=90pc)

2. Nếu là lần đầu truy cập vào **Directory Services** ở vùng này, bạn sẽ được dẫn đến màn hình chào khởi đầu. Mở rộng thanh bên trái và chọn **Directories**.

   - Chọn **Set up directory**.

   ![Hình ảnh](/images/4-AD/0002.png?featherlight=false&width=90pc)

3. Thực hiện chọn **Directory types**, chọn **AWS Managed Microsoft AD**.

   ![Hình ảnh](/images/4-AD/0003.png?featherlight=false&width=90pc)

4. Trong trang **Enter Directory Information**, nhập vào các thông tin sau:

   - Ở **Edition**: chọn **Standard Edition**.

   - Ở **Directory DNS name**: onprem.example.com (tên **DNS** này phải là duy nhất trong số các directory của bạn).

   - Ở **Directory NetBIOS name**: onprem (tên **NetBIOS** này phải là duy nhất trong số các directory của bạn).

   ![Hình ảnh](/images/4-AD/0004.png?featherlight=false&width=90pc)

5. Tiếp tục cấu hình:

   - Ở **Directory Description**: This is to simulate the on-prem AD.

   - Ở **Admin Password**: Sử dụng mật khẩu bạn có thể nhớ. Vui lòng chú ý các yêu cầu về độ phức tạp của mật khẩu được nêu trên màn hình.

   - Ở **Confirm password**: Nhập lại mật khẩu một lần nữa.

   - Chọn **Next**.

   ![Hình ảnh](/images/4-AD/0005.png?featherlight=false&width=90pc)

6. Ở **Choose VPC and subnets**, chọn **VPC Hybrid-DNS-VPCStack** mà chúng ta đã tạo từ trước và hai private subnet **Private subnet 1A** và **Private subnet 2A**. Sau đó, chọn **Next**.

   ![Hình ảnh](/images/4-AD/0006.png?featherlight=false&width=90pc)

7. Ở màn hình **Review & create**, xem lại thiết lập và chọn **Create Directory**.

   ![Hình ảnh](/images/4-AD/0007.png?featherlight=false&width=90pc)

8. Directory sẽ mất khoảng 20 phút để tạo. Trong thời gian này, AWS sẽ cung cấp hai máy chủ **Windows** và nâng chúng trở thành **Active Directory** domain controllers cho AD forest mà bạn đã chỉ định. AD forest này sẽ là một AD forest mới. Quá trình sẽ hoàn tất khi bạn thấy trạng thái chuyển sang Active.

   ![Hình ảnh](/images/4-AD/0008.png?featherlight=false&width=90pc)

9. Khi directory đã được tạo, bạn có thể xem chi tiết bằng cách nhấp vào **Directory ID**. Hai địa chỉ IP của **DNS** được liệt kê là địa chỉ IP của **elastic network interfaces** (ENI) đã được đặt trong availability zone của bạn để giao tiếp với **AWS Managed Microsoft AD Domain Controllers**.

   ![Hình ảnh](/images/4-AD/0009.png?featherlight=false&width=90pc)
