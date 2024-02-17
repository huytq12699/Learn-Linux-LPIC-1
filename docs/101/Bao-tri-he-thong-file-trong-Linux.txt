#Bảo trì hệ thống file trong Linux

-`fsck` Tiện ích kiểm tra file system. Có thể được gọi thông qua dòng lệnh và đc cấu hình trong file `/etc/fstab`.
Thiết bị phải được unmount trước khi fsck chạy để kiểm tra

-`e2fsck` Tiện ích kiểm tra file system cho các file system ext2, ext3 và ext4. Có thể đc sử dụng để chạy kiểm tra
lại file systems

-`mke2fs` Tiện ích để tạo các file systems ext2, ext3 và ext4 mới

-`tune2fs` Tiện ích được sử dụng để điều chỉnh các thông số trên các file systems ext2, ext3 hoặc ext4

-`xfs_repair` Tiện ích được sử dụng để sửa chữa các file system XFS

-`xfs_fsr` Sắp xếp lại dữ liệu được lưu trữ trong các khối trên file systems XFS
Tương tự như chạy tiện ích defrag trên hệ thống tệp MS Windows

-`xfs_db` Tiện ích được sử dụng để gỡ lỗi (debug) file system XFS