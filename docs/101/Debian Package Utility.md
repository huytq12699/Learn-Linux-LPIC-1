# DEBIAN PACKAGE UTILITY(dpkg)

Gói cài đặt `.deb` gồm:

- ứng dụng hoặc tiện ích

- file cấu hình mặc định

- các hướng dẫn cách thức và nơi cài đặt các files đi kèm với package

- liệt kê các dependencies mà package cần có
Dependencies cần cho package đã được cài đặt, hoặc được cài đặt với package

- `apt` xử lý cài đặt dependencies cho bạn, `dpkg` không xử lý.

## Các câu lệnh với `dpkg`

- `dpkg --info` Hiển thị các thông tin một package

- `dpkg --status` Giống như lên --info nhưng ít thông tin chi tiết của package hơn

- `dpkg -l` Liệt kê các gói khớp với chuỗi được cung cấp

- `dpkg -i` Cài đặt một hoặc nhiều gói packages cụ thể

- `dpkg -L` Liệt kê tất cả các file đã được cài đặt của một gói cụ thể

- `dpkg -r` Gỡ bỏ(xóa) một package cụ thể nhưng không xóa các files cấu hình

- `dpkg -P` Xóa bỏ một package cụ thể và cũng xóa bỏ các file cấu hình đã được cài đặt vào HĐH

- `dpkg -S` Tìm kiếm package database cho một file cụ thể và liệt kê các gợi ý của file với
một chuỗi cụ thể

- `dpkg -reconfigure` Cho phép sự sửa đổi của một package bằng cách chạy lại công cụ cấu hình của
ứng dụng