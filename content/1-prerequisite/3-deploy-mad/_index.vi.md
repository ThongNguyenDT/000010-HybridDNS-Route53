+++
title = "Triển khai Microsoft AD"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3. </b>"
+++

**Nội dung:**
- [AWS Managed Microsoft Active Directory](#aws-managed-microsoft-active-directory)

#### AWS Managed Microsoft Active Directory

Để **giả lập DNS on-premise**, chúng ta sẽ sử dụng dịch vụ **AWS Managed Microsoft Active Directory** trong bài thực hành này.

1. Đăng nhập vào **AWS Console** và truy cập vào **Directory Service console** thông qua khung tìm kiếm và tìm **Directory Services**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn Asia Pacfic (Tokyo))
3. Nếu là lần đầu truy cập vào Directory Services ở region, bạn sẽ được dẫn đến màn hình chào khởi đầu. Chọn **“AWS Managed Microsoft AD”** và chọn **Set up directory**.
4. Ở trang kế tiếp, chọn **“AWS Managed Microsoft AD”** và chọn **Next**.

![Deploy MAD](../../../images/1/5-mad.png?width=90pc)

5. Trong trang **Enter Directory Information**, nhập vào các thông tin sau:
   - Ở **Edition**: chọn **Standard Edition**.
   - Ở **Directory DNS name**: onprem.example.com [Đặt tên DNS này là **duy nhất** cho các directory khác của bạn để bạn có thể thiết lập trust trong tương lai nếu cần thiết.]
   - Ở **Directory NetBIOS name**: onprem [Đặt tên NETBIOS này là **duy nhất** cho các directory khác của bạn để bạn có thể thiết lập trust trong tương lai nếu cần thiết]
   - Ở **Directory Description**: This is to simulate the on-prem AD.
   - Ở **Admin password**: Sử dụng mật khẩu bạn có thể nhớ. Bạn sẽ sử dụng nó trong các phần tiếp theo. 
   {{% notice info %}}
   Vui lòng chú ý các yêu cầu về độ phức tạp của mật khẩu được nêu trên màn hình.
   {{% /notice %}}
   - Ở **Confirm password**: Nhập lại mật khẩu một lần nữa.
   - Chọn **Next**.

![Deploy MAD](../../../images/1/5-mad2.png?width=90pc)

6. Ở **VPC and subnets**, chọn VPC **HybridDNS-VPCStack** mà chúng ta đã tạo từ trước và hai private subnet **Private subnet vv1A** và **Private subnet 2A**.
7. Sau khi lựa chọn **VPC and Subnets**, Chọn **Next**.

![Deploy MAD](../../../images/1/5-mad3.png?width=90pc)

8. Ở màn hình **Review & create**, xem lại thiết lập và chọn **Create Directory**.

![Deploy MAD](../../../images/1/5-mad4.png?width=90pc)

9. Directory sẽ mất khoảng 20 phút để tạo. Trong thời gian này, AWS sẽ cung cấp hai máy chủ Windows và nâng chúng trở thành Active Directory domain controllers cho AD forest mà bạn đã chỉ định. AD forest này sẽ là một AD forest mới.
10.  Quá trình sẽ hoàn tất khi bạn thấy trạng thái chuyển sang **Active**. Khi directory được tạo, bạn có thể xem chi tiết bằng cách nhấp vào **Directory ID**. Hai **địa chỉ IP của DNS** được liệt kê là địa chỉ IP của elastic network interfaces (ENI) đã được đặt availability zone của bạn để giao tiếp với **AWS Managed Microsoft AD Domain Controllers**.

![Deploy MAD](../../../images/1/5-mad5.png?width=90pc)
