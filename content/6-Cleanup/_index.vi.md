---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Dọn dẹp tài nguyên

#### Xóa inbound endpoint

- Truy cập vào Route 53 Management Console
- Ở thanh bên trái, chọn Inbound endpoints
- Tick vào Inbound endpoint liên quan tới bài lab
- Chọn **Delete**
- Gõ **Delete** vào ô trống và nhấn Submit

#### Xóa Resolver Rule

  - Truy cập vào Route 53 Management Console
  - Ở thanh bên trái, chọn Rules
  - Chọn vào Rule liên quan tới bài lab để vào trang thông tin của Rule
  - Ở mục VPCs, tick vào VPC đang được kết nối với Rule và chọn Disassociate
  - Gõ disassociate vào ô trống và chọn Submit
  - Đợi 1-2 phút để ngắt kết nối với VPC đó.
  - Trong trang thông tin của Rule, chọn **Delete**
  - Gõ **Delete** vào ô trống và nhấn Submit

#### Xóa **Outbound Endpoint**

  - Truy cập vào Route 53 Management Console
  - Ở thanh bên trái, chọn Outbound Endpoint**s**
  - Tick vào **Outbound Endpoint** liên quan tới bài lab
  - Chọn **Delete**
  - Gõ **Delete** vào ô trống và nhấn Submit

#### Xóa AWS Managed Microsoft Active Directory

  - Truy cập vào Directory Service Management Console
  - Ở thanh bên trái, chọn Directories
  - Tick vào Directory liên quan tới bài lab
  - Chọn Actions và chọn **Delete** directory
  - Gõ tên miền **DNS** của directory vào ô trống và nhấn **Delete**

#### Xóa CloudFormation Stack - khi bạn xóa CloudFormation Stack, các tài nguyên được tạo bởi stack đó đều được xóa.

  - Trong trường hợp này, stack Hybrid**DNS** đã tạo ra hai stack con (nested stack), và khi bạn xóa stack Hybrid**DNS**, hai stack con cũng được xóa theo.
  - Truy cập vào CloudFormation Management Console
  - Ở thanh bên trái, chọn Stacks
  - Tick vào stack Hybrid**DNS** và chọn **Delete**
  - Trong prompt, chọn **Delete** stack
  - Đợi vài phút cho tới khi CloudFormation xóa bỏ hết tài nguyên