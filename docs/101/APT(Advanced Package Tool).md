# APT(Advanced Package Tool)

- APT là công cụ quản lý các gói cấp cao của các hệ điều hành Ubuntu và Debian, là một trong những công cụ quản lý packages cấp cao phổ biến nhất hiện nay.
- Có thể sử dụng APT để cài đặt các ứng dụng và các dependencies của ứng dụng.
- Xóa ứng dụng(Remove applications)
- Cập nhật(Updates) và nâng cấp(Upgrade) phiên bản của các gói phần mềm đã được cài đặt trong hệ điều hành lên phiên bản mới nhất.

## Căn bản về lệnh APT hoạt động như thế nào?
- Đọc file `/etc/apt/sources.list`
- Cài đặt(installation) và xóa, gỡ bỏ phần mềm ứng dụng trong hệ điều hành.

### Các câu lệnh APT

`/etc/apt/sources.list` là file cấu hình liệt kê các vị trí kho lưu trữ các gói phần mềm.

`apt-get update` cập nhật bộ nhớ đệm apt cục bộ bằng danh sách các gói có thể được cập nhật/nâng cấp 
và cài đặt hệ điều hành.

`apt-get upgrade` nâng cấp các gói phần mềm có sẵn bản nâng cấp 

`apt-get install` cài đặt một gói từ các kho lưu trữ(repositories) có trong sources file

`apt-get remove` xoá một gói trong hệ điều hành nhưng vẫn giữ nguyên các files cấu hình liên quan 
đến gói này.

`apt-get purge` xoá một gói trong hệ điều hành và các file cấu hình liên quan đến gói này 

`apt-get dist-upgrade` nâng cấp tất cả hệ thống lên phiên bản mới nhất

`apt-get download` tải xuống một gói mà không cài đặt nó

`apt-cache search` Tìm kiếm thông qua bộ đệm apt cục bộ của hệ điều hành để tìm gói có thể được cài đặt

`apt-cache show` Hiển thị thông tin căn bản về một gói

`apt-cache showpkg` Hiện thị thêm chi tiết các thông tin kỹ thuật và một gói
