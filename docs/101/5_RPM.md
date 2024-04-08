# RPM (Quản lý package sử dụng RPM)

1. Gói (package) cài đặt `.rpm` gồm:

- Ứng dụng hoặc tiện ích

- Files cấu hình mặc định

- Các hướng dẫn cách thức và nơi cài đặt các files đi kèm với package

- Liệt kê các dependencies mà package cần có

2. RPM Database

- Lưu trữ trong `/var/lib/rpm`

- Sử dụng lệnh `rpm --rebuilddb` để sửa cơ sở dữ liệu rpm bị hỏng, Dependencies cần cho package đã được cài đặt 
hoặc được cài đặt với package

- `yum` xử lý cài đặt dependencies cho bạn, `rpm` không xử lý

## Các lệnh RPM

+ `rpm -qpi` Hiển thị thông tin của một package

+ `rpm -qpl` Liệt kê tất cả các files trong 1 package

+ `rpm -qa` Hiển thị tất cả các packages đã được cài đặt trong hệ điều hành

+ `rpm -i` Cài đặt một package cụ thể, thường được kết hợp với các tùy chọn khác 
để cung cấp thêm thông tin đầu ra về quá trình cài đặt. VD: rpm -ivh

+ `rpm -U` Nâng cấp một package đã cài đặt lên phiên bản mới nhất

+ `rpm -e` Gỡ, xóa bỏ một package đã được cài đặt vào hệ điều hành

+ `rpm -Va` Xác nhận tất cả các packages đã được cài đặt

+ `rpm2cpio` Chuyển đổi một `.rpm` file trong 1 file lưu trữ cpio, thường được phối hợp với lệnh `cpio`

```sh
 		VD: rpm2cpio name.rpm | cpio -idmv
```
