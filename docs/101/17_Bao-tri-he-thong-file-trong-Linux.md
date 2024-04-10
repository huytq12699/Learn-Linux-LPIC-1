# Bảo trì hệ thống file trong Linux

1. Lệnh `du`

- Được sử dụng để 'ước tính' việc sử dụng dung lượng ổ đĩa(hard disk) cho các files hoặc thư mục  

- `-a (hoặc --all)`: hiển thị số lượng cho tất cả các files, không chỉ thư mục

- `-c (hoặc --total)`: tính tổng cộng

- `-h (hoặc --human-readable)`: hiển thị kích thước dưới dạng đọc được (K/M/G/TB)

- `-s (hoặc --summarize)`: chỉ hiển thị tổng kết cho mọi đối số

- Lưu ý: có thể sử dụng với globbing file  

- Ví dụ: 
	
	```sh
	du -sh /home/user/.bash* 
	```
	+ Sẽ cung cấp một tóm tắt dễ đọc cho mỗi file hoặc thư mục phù hợp với `.bash*` trong thư mục /home/user

2. Lệnh `df`

- Báo cáo việc sử dụng dung lượng ổ đĩa(hard disk) của filesystem.  

- `-a (hoặc --all)`: bao gồm tất cả các filesystem (bao gồm cả filesystems 'dummy').  

- `--direct`: hiển thị thống kê cho một file thay vì mount.  

- `--total`: hiển thị tổng cộng.

- `-h (hoặc --human-readable)`: hiển thị kích cỡ dung lượng ổ dưới dạng đọc được (K/M/G/TB).

- `-l (hoặc --local)`: chỉ bao gồm các filesystem cục bộ.

- `-t (hoặc --type)`: giới hạn danh sách cho loại được chỉ định.

- Ví dụ: 

	```sh
	df -lh --total  
	```
	+ Sẽ tạo ra một danh sách dễ đọc được của tất cả các filesystems cục bộ bao gồm một dòng tổng kết ở cuối. 

3. Lệnh `debugfs`

- Trình gỡ lỗi filesystem, có thể hiển thị một lượng thông tin lớn về phân vùng được chỉ định.  

- Ví dụ: 

	```sh
	debugfs /dev/sdb1  
	```
	+ Sẽ hiển thị nhiều thông tin về bất kỳ file hoặc thư mục nào đã được chỉ định chọn trên ổ đĩa   

- Tương tác (sau khi bắt đầu)

	+ `?`: hiển thị các lệnh có sẵn  

	+ `cd [đường dẫn]`: chuyển đến đường dẫn đã chỉ định (LƯU Ý: phải tồn tại trên ổ đĩa mà debugfs đang chạy)  
	
	+ `features`: hiển thị các tính năng của filesystem  
	
	+ `logdump`: hiển thị nội dung nhật ký (nếu có sẵn)  

	+ `ls`: hiển thị nội dung của thư mục hiện tại  
	
	+ `pwd`: hiển thị thư mục làm việc  
	
	+ `open`: mở một filesystem để gỡ lỗi  
	
	+ `stats`: hiển thị thống kê cho filesystem 
	
	+ `undelete`: khôi phục tệp đã bị xóa (Lưu ý: PHẢI được sử dụng ngay sau khi xóa file trước khi tất cả các thay đổi được đồng bộ hóa với ổ đĩa, thường không tìm thấy file đã bị xóa trên các phiên bản hiện đại vì 'sync' là cài đặt mặc định cho đồng bộ hóa đĩa của filesystem)

	+ `quit`: exit 

4. Lệnh `fsck`

- Kiểm tra filesystem

	- `e2fsck` - kiểm tra các loại filesystem 'ext'

	- `reiserfsck` - kiểm tra các loại filesystem 'ReiserFS' 

	- `dosfsck` - kiểm tra các loại filesystem DOS (ví dụ VFAT)

- Sử dụng /etc/fstab để kiểm tra các filesystems tự động khi khởi động (những filesystems có '1' ở cột thứ sáu trong file), khi một filesystem được đánh dấu là 'unclean' (bị crash, hỏng, không được unmount một cách sạch sẽ, v.v.), một lệnh scan quét sâu hơn sẽ được thực hiện.

- Nếu filesystem không thể được sửa chữa tự động khi khởi động, bạn sẽ được nhắc nhở phải nhấn 'CTRL-D' để tiếp tục hoặc cung cấp mật khẩu root để thực hiện quét sâu hơn (hiển thị lời nhắc cứu hộ).   

- `-A` - fsck sẽ lặp lại qua file /etc/fstab và kiểm tra tất cả các filesystem

- `-C` - hiển thị thanh tiến trình băm/dấu

- `-N` - chạy thử, không thực hiện thay đổi nhưng hiển thị những gì sẽ được thực hiện 

- `-V` - đầu ra chi tiết (cẩn thận, rất nhiều thông tin và có thể cuộn để xem thông tin)

- `-a` - chỉ thực hiện mà không yêu cầu xác nhận hoặc phản hồi khác, chạy kiểm tra và sửa chữa một cách phi tương tác

- `-f` - bắt buộc kiểm tra ngay cả khi filesystem báo cáo là sạch sẽ

- Thứ tự các sự kiện kiểm tra của `fsck`:

	+ b1. Kiểm tra inode, khối, kích thước 
	
	+ b2. Kiểm tra cấu trúc thư mục 
	
	+ b3. Kiểm tra kết nối thư mục 
	
	+ b4. Kiểm tra số lượng tham chiếu của tệp/thư mục 
	
	+ b5. Kiểm tra thông tin tóm tắt của nhóm  

5. Lệnh `tune2fs`

- Sử dụng để đặt các tham số filesystem sau khi tạo. 

- `-c [#]`: đặt số lần tối đa mà một filesystem có thể được gắn kết để fsck tự động xảy ra 

- `-e [option]`: thay đổi hành vi của filesystem với tùy chọn được chỉ định (tiếp tục, remount-ro, panic)

- `-g [tênnhóm]`: thêm nhóm được chỉ định như là người dùng tiềm năng của dung lượng dự trữ trên filesystem (thường dành cho root)

6. `xfsprogs`

- Công cụ và tiện ích cho filesystem XFS

7. `xfs_check` 

- Tương đương fsck cho filesystem XFS để kiểm tra filesystem

8. `xfs_repair`

- Tương đương fsck cho filesystem XFS để sửa chữa filesystem 

9. `xfs_metadump`

- Tạo thông tin gỡ lỗi có thể được sử dụng bởi một bên thứ ba để hỗ trợ khôi phục một filesystem XFS khi quá trình sửa chữa thất bại  

10. `xfs_growfs`

- Được sử dụng để mở rộng một filesystem XFS (tuy nhiên, không thể thu nhỏ)    
