#Phân vùng Legacy MBR

-`lsblk` Lệnh được sử dụng để liệt kê các thiết bị lưu trữ. Ví dụ như ổ đĩa cứng

-`fdisk` Lệnh cũ được sử dụng để tạo phân vùng chuẩn MBR (DOS)

-`parted` Lệnh hiện đại được sử dụng để tạo phân vùng cho ổ cứng chuẩn MBR hoặc GPT

- Partition ID:
	+ 83 - hệ thống tệp hệ điều hành Linux tiêu chuẩn
	+ 82 - phân vùng swap Linux
	+ 8e - LVM linux Volume