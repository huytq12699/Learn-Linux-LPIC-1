# Trang hướng dẫn(man page) trong Linux

- Cung cấp trang hướng dẫn tích hợp sẵn cho các lệnh, files cấu hình và các tác vụ 
quản trị hệ thống

- Gọi với cú pháp: `man[tên lệnh]`

- Trang hướng dẫn được chia thành các 'phần'(sections):

	+ Phần 1: các chương trình thực thi hoặc lệnh, dòng lệnh(shell commands)

	+ Phần 2: system calls - các hàm được cung cấp bởi kernel

	+ Phần 3: library calls - các hàm trong các thư viện chương trình

	+ Phần 4: các file đặc biệt(special files) - thường đc tìm thấy trong thư mục `/dev`

	+ Phần 5: định dạng và quy ước file(file formats and conventions)
			ví dụ như file `/etc/passwd` và các file cấu hình khác

	+ Phần 6: trò chơi

	+ Phần 7: các mục và quy ước đa dạng(miscellaneous items and conventions)
			ví dụ như man(7), regex(7)

	+ Phần 8: các lênh quản trị hệ thống(system administrator commands) - thường chỉ dành cho `root`

	+ Phần 9: các thủ tục kernel(không chuẩn)

## Các câu lệnh trong Man page

`man` Lệnh dùng để mở trang(manual page) cho một câu lệnh cụ thể

`man -k` Được sử dụng để tìm kiếm các trang hướng dẫn cho một từ khóa cụ thể

`apropos` Liên quan, liên kết đến lệnh `man -k`

`man [số chương]` Mở một số chương cụ thể cho một lệnh cụ thể 