+++
title = "Dọn dẹp tài nguyên"
date = 2021-06-30T09:50:13+07:00
weight = 3
chapter = false
pre = "<b>3. </b>"
+++
1. **Xóa inbound endpoint**
    - Truy cập vào Route 53 Management Console
    - Ở thanh bên trái, chọn Inbound endpoints
    - Tick vào Inbound endpoint liên quan tới bài lab
    - Chọn Delete
    - Gõ delete vào ô trống và nhấn Submit
2. **Xóa Resolver Rule**
    - Truy cập vào Route 53 Management Console
    - Ở thanh bên trái, chọn Rules
    - Chọn vào Rule liên quan tới bài lab để vào trang thông tin của Rule
    - Ở mục VPCs, tick vào VPC đang được kết nối với Rule và chọn Disassociate
    - Gõ disassociate vào ô trống và chọn Submit
    - Đợi 1-2 phút để ngắt kết nối với VPC đó.
    - Trong trang thông tin của Rule, chọn Delete
    - Gõ delete vào ô trống và nhấn Submit
3. **Xóa outbound endpoint**
    - Truy cập vào Route 53 Management Console
    - Ở thanh bên trái, chọn Outbound endpoints
    - Tick vào Outbound endpoint liên quan tới bài lab
    - Chọn Delete
    - Gõ delete vào ô trống và nhấn Submit
4. **Xóa AWS Managed Microsoft Active Directory**
    - Truy cập vào Directory Service Management Console
    - Ở thanh bên trái, chọn Directories
    - Tick vào Directory liên quan tới bài lab
    - Chọn Actions và chọn Delete directory
    - Gõ tên miền DNS của directory vào ô trống và nhấn Delete
5. **Xóa CloudFormation Stack** - khi bạn xóa CloudFormation Stack, các tài nguyên được tạo bởi stack đó đều được xóa. Trong trường hợp này, stack **HybridDNS** đã tạo ra hai stack con (*nested stack*), và khi bạn xóa stack **HybridDNS**, hai stack con cũng được xóa theo.
    - Truy cập vào CloudFormation Management Console
    - Ở thanh bên trái, chọn Stacks
    - Tick vào stack **HybridDNS** và chọn Delete
    - Trong prompt, chọn Delete stack
    - Đọi vài phút cho tới khi CloudFormation xóa bỏ hết tài nguyên
