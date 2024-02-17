# Phân vùng GPT Partitions

-`lsblk` Lệnh được sử dụng để liệt kê các thiết bị lưu trữ. Ví dụ như ổ đĩa cứng

-`gdisk` Đây là một lệnh giống `fdisk` được sử dụng để tạo các phân vùng GPT trong ổ cứng

-`parted` Lệnh hiện đại được sử dụng để tạo phân vùng cho ổ cứng chuẩn MBR hoặc GPT

- Partition ID:
	+ 8300 - hệ thống tệp hệ điều hành Linux tiêu chuẩn
	+ 8200 - phân vùng swap Linux
	+ 8e00 - LVM Linux Volume