# Thiết đặt môi trường Shell

`/etc/profile` Đây là file được đọc đầu tiên trong một phiên đăng nhập.
Nó thiết lập các biến môi trường trên toàn hệ điều hành, giá trị umask, kiểm soát lịch sử Bash(history), ...
```sh
	less /etc/profile
	```

`/etc/profile.d` Đây là thư mục chứa các file script cấu hình bổ sung cho Bash

`/etc/bashrc` Trong file này, bạn có thể cấu hình các chức năng và alias trên toàn hệ thống
```sh
	less /etc/bashrc
	```

`/etc/skel` Đây là thư mục chứa các file mặc đinh như `.bash_profile`, `.bashrc` và 
các file khác được thêm vào thư mục `home` của người dùng khi tài khoản được tạo trên HĐH

`~/.bash_profile` File này có thể chứa biến môi trường PATH được sửa đổi của người dùng và 
sẽ kế thừa nội dung từ file `~/.bash.rc`

`~/.bash_logout` File này được gọi khi người dùng đăng xuất và có thể được sử dụng để tắt ứng dụng, 
hiển thị thông điệp hoặc thực hiện các tác vụ dọn dẹp môi trường khác

`~/.bash_login` File này được gọi khi người dùng đăng nhập. 
Thông thường, các file `.bash_profile` và `.bashrc` được sử dụng thay vì file này
