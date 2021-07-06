+++
title = "Triển khai Microsoft AD"
date = 2020
weight = 3
chapter = false
pre = "<b>1.3. </b>"
+++

Để **giả lập DNS on-premise**, chúng ta sẽ sử dụng dịch vụ **AWS Directory Service** để triển khai **AWS Managed Microsoft Active Directory** trong hai private subnet được tạo bởi CloudFormation như hình dưới đây:
![Overview Diagram](../../../images/1/Architecture-1_PreReq.png?width=40pc)

**Nội dung:**
- [AWS Managed Microsoft Active Directory](#aws-managed-microsoft-active-directory)

#### AWS Managed Microsoft Active Directory

1. Đăng nhập vào **AWS Console** và truy cập vào **Directory Service console** thông qua khung tìm kiếm và tìm **Directory Services**.
2. Hãy chắc chắn bạn đã chọn đúng Region. Chú ý ở góc trái của AWS Console và lựa chọn đúng Region mà bạn cần (Ở đây chúng ta đang lựa chọn **ap-southeast-1**)
3. Nếu là lần đầu truy cập vào Directory Services ở region, bạn sẽ được dẫn đến màn hình chào khởi đầu. Mở rộng thanh bên trái và chọn **Directories**.
4. Chọn **Set up directory**.

![1.3_SetUpDir](../../../images/1/1.3_SetUpDir.png?width=90pc)

5. Trong trang **Enter Directory Information**, nhập vào các thông tin sau:
   - Ở **Edition**: chọn **Standard Edition**.
   - Ở **Directory DNS name**: onprem.example.com (*tên DNS này phải là duy nhất trong số các directory của bạn*).
   - Ở **Directory NetBIOS name**: onprem (*tên NetBIOS này phải là duy nhất trong số các directory của bạn*).
   - Ở **Directory Description**: This is to simulate the on-prem AD.
   - Ở **Admin password**: Sử dụng mật khẩu bạn có thể nhớ. Vui lòng chú ý các yêu cầu về độ phức tạp của mật khẩu được nêu trên màn hình.
   
   - Ở **Confirm password**: Nhập lại mật khẩu một lần nữa.
   - Chọn **Next**.

![1.3_EnterDirInfo](../../../images/1/1.3_EnterDirInfo.png?width=90pc)

6. Ở **Choose VPC and subnets**, chọn VPC **HybridDNS-VPCStack** mà chúng ta đã tạo từ trước và hai private subnet **Private subnet 1A** và **Private subnet 2A**. Sau đó, chọn **Next**.

![1.3_ChooseVPC](../../../images/1/1.3_ChooseVPC.png?width=90pc)

7. Ở màn hình **Review & create**, xem lại thiết lập và chọn **Create Directory**.

8. Directory sẽ mất khoảng 20 phút để tạo. Trong thời gian này, AWS sẽ cung cấp hai máy chủ Windows và nâng chúng trở thành Active Directory domain controllers cho AD forest mà bạn đã chỉ định. AD forest này sẽ là một AD forest mới. Quá trình sẽ hoàn tất khi bạn thấy trạng thái chuyển sang **Active**
9. Khi directory đã được tạo, bạn có thể xem chi tiết bằng cách nhấp vào **Directory ID**. Hai **địa chỉ IP của DNS** được liệt kê là địa chỉ IP của elastic network interfaces (ENI) đã được đặt availability zone của bạn để giao tiếp với **AWS Managed Microsoft AD Domain Controllers**.
{{% notice note %}}
Hãy ghi nhớ hai địa chỉ IP của directory đã được tạo để sử dụng cho phần sau.
{{% /notice %}}
![1.3_DirIP](../../../images/1/1.3_DirIP.png?width=90pc)
