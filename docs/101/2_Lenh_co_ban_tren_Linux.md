# Lệnh cơ bản trên hệ thống Linux

- `#exit` hoặc `#logout` : thoát ra khỏi trạng thái đăng nhập

- `#ps`: Liệt kê các tiến trình đang hiện hành và PID (Process ID) của tiến trình đó.

- `#sleep <thoi_gian>`: Cho phép hệ thống ngừng hoạt động trong một thời gian (thời gian tính bằng giây).

	+ Ví dụ:

	```sh
	sleep 6
	```
	+ Máy chủ sẽ tạm thời ngưng hoạt động trong 6 giây.

- `#useradd <ten_user>`: Thêm 1 user vào hệ thống

- `#passwd <ten_user>`: Cập nhật mật khẩu cho user đã tạo.

- `#who`: Cho biết user nào đang sử dụng hệ thống

- `#whoami`: Cho biết user nào đang đăng nhập

- `#top`: Hiển thị các tiến trình đang chạy trên hệ thống. Tương tự như `Task manager` của Hệ điều hành Windows

- `#usermod -aG wheel <username>`: Cho phép user sử dụng quyền sudo

- `#su - <username>`: Đăng nhập bằng user khác

- Nhấn tổ hợp `ctrl + L` hoặc `#clear` đề làm sạch Commandline.

- `# history`: Để xem lịch sử các lệnh đã được thực thi bởi user hiện tại

- `# pwd`: Hiển thị đường dẫn tại nơi hiện hành

- `# date`: Kiểm tra ngày giờ trên máy

- `free`: Kiểm tra RAM của máy

	+ `-b`: Hiển thị dưới dạng byte

	+ `-k`: Hiển thị dưới dạng Kb

	+ `-m`: Hiển thị dưới dạng Mb

	+ `-g`: Hiển thị dưới dạng Gb

- `# hostnamectl`: Xem thông tin hostname hiện tại của máy

- `# uname`: Kiểm tra hệ điều hành đang sử dụng

- `# yum update`: Cập nhật hệ thống

- `# init 0`: Tắt máy

- `# init 6`: Khởi động lại hệ thống

- `#reboot`: Khởi động lại hệ thống ~ `init 6`

- `# w`: Kiểm tra các phiên SSH

- `# df -h`: Hiển thị dung lượng ổ cứng của máy (dung lượng sẵn sàng và được sử dụng...)

- `# df -i`: Hiển thị thông tin Inodes của máy (tổng số file đã tạo ra, số file còn có thể tạo, số file đã tạo...)