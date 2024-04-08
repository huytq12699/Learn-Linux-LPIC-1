# YUM

### Mô tả về Yum:

- Xử lý các RPM package dependencies

- Cài đặt, nâng cấp và xóa package

- Được sử dụng cho các hệ điều hành: Red Hat Enterprise(RHEL), CentOS, Scientific Linux 
và các phiên bản cũ của Fedora

### Yum setup

- Các tùy chọn cấu hình được thiết đặt trong file `/etc/yum.conf`

- Đọc các thông tin của kho lưu trữ từ các files trong `/etc/yum.respon.d`

- Các bộ đệm( caches) lưu Thông tin kho lưu trữ được cập nhật mới nhất trong `/var/cache/yum`

### Các công cụ quản lý RPM khác

- ZYPPER

	+ Được sử dụng cho SUSE Linux distributions

	+ Vd: 

			`zipper repos`

			`zipper install vim`

- DNF (DNDIFIED YUM)

	+ Được sử dụng trong HĐH Linux Fedora distributions

	+ Tương lai sẽ thay thế yum trong Red Hat EnterPrise Linux

	+ Cú pháp câu lệnh sử dụng giống như Yum

## Các câu lệnh YUM

- `yum update` Tìm kiếm các kho lưu trữ trực tuyến để tìm các packages được cập nhật so với 
những gì hiện được cài đặt trên hệ thống, nâng cấp các packages trong hệ điều hành.

- `yum search` Tìm kiếm các kho lưu trữ cho một package cụ thể

- `yum info` Liệt kê thông tin về một package cụ thể

- `yum list installed` Hiện thị tất cả các thông tin về các gói đã được cài đặt vào hệ điều hành

- `yum clear all` Xóa tất cả thông tin bộ đệm (cache) của Yum và database cục bộ của nó

- `yum install` Cài đặt một package cụ thể và tất cả các dependencies của package

- `yum remove` Gỡ, xóa một package nhưng vẫn giữ các dependencies

- `yum autoremove` Gỡ, xóa một package và tất cả các dependencies

- `yum whatprovides` Tìm kiếm một package có 1 tên file cụ thể

- `yum reinstall` Cài đặt lại một package cụ thể