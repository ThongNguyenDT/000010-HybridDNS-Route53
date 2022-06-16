---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

#### Các bước chuẩn bị

#### Tổng quan

Bước đầu tiên bạn sẽ xây dựng cơ sở hạ tầng mạng trong AWS. Trong phần này, bạn sẽ tận dụng **AWS Quick Start**để xây dựng một hạ tầng mạng có tính sẵn sàng cao (HA) và bảo mật. Sau đó, bạn sẽ triển khai thêm một **AWS Managed Microsoft Active Directory** bằng dịch vụ **AWS Directory Service** để mô phỏng cho hệ thống **DNS** on-prem của bạn. Khi hoàn thành xong phần này, bạn sẽ triển khai thành công kiến trúc hạ tầng như sau:

![Set up](/images/2-Pre/0001.png?featherlight=false&width=60pc)

#### **AWS Quick Starts**

**AWS Quick Starts** là một thư viện chứa những template kiến trúc được xây dựng sẫn bởi những **Solution Architects và Partner của AWS**. **AWS Quick Starts** sử dụng **AWS CloudFormation** làm công cụ xây dựng nên những kiến trúc được viết trong những template của mình.

#### **AWS CloudFormation**

**AWS CloudFormation** là dịch vụ **Infrastructure as Code (IaC)** của AWS cho phép bạn tạo hạ tầng dựa trên template (được viết bằng **YAML** hoặc JSON). **Template** được tải lên dịch vụ CloudFormation và tự động tạo cơ sở hạ tầng được mô tả trong template.

#### **AWS Directory Service**

**AWS Directory Service** là một công cụ cho phép bạn triển khai một **Active Directory** ngay trên AWS Cloud để phục vụ cho việc đơn giản hóa công tác quản lý và cung cấp quyền truy cập cho end user tới các dịch vụ của AWS.

#### **Nội dung**

1. [Tạo Key Pair](2.1-createkeypair/)
2. [Khởi động CloudFormation Template](2.2-launchcloudformation/)
3. [Cấu hình Security Group](2.3-security/)