# Gắn filesystem thủ công và tự động

### Lệnh `/mnt`  

- Thư mục 'cha' đa năng thường được sử dụng để gắn kết ổ đĩa/phân vùng không thuộc filesystem cài đặt hoặc nằm ngoài cấu trúc 'root' của hệ điều hành. 
(ví dụ, ổ sao lưu hoặc ổ đĩa dữ liệu thường)

###  Lệnh `blkid`  
 
- Lệnh sử dụng để lấy UUID (định danh duy nhất chung) cho các phân vùng ổ đĩa cục bộ trên hệ thống Linux, cũng sẽ hiển thị labels (nếu có)  

- Bằng giá trị với UUID lấy được trong `/dev/disk/by-uuid`


### Lệnh `mount` 

- Được sử dụng để gắn(mount) hệ thống tập tin vào một điểm gắn(mount point), thường là một thư mục

- Khi lệnh này thực thi mà không có tham số, sẽ hiển thị các filesystems được gắn vào Linux (đọc từ `/etc/mtab`, cũng có sẵn trong `/proc/mounts`)  

- Lệnh được sử dụng để gắn mount thủ công một thiết bị với một filesystem hiện có trên một điểm gắn kết (thư mục)  

- `-a`: gắn mount tất cả các filesystems trong `/etc/fstab` (nếu chưa được gắn mount, sẽ KHÔNG gỡ bỏ/mount lại những filesystems đã được mount)  

- `-f`: giả lập gắn mount tất cả các filesystems trong `/etc/fstab`  

- `-r`: gắn mount filesystem chỉ định ở chế độ chỉ đọc  

- `-t [fstype]`: loại filesystem để gắn mount thiết bị được chỉ định (có thể đọc thông qua các giá trị trong superblock tự động nếu kernel hỗ trợ filesystem đó)  

- `-o [option(s)]`: chỉ định một hoặc nhiều tùy chọn nằm ngoài các giá trị mặc định (xem `/etc/fstab` cột 4)  

- `-w`: gắn mount ở chế độ có thể ghi (mặc định) 

### Lệnh `umount` 

- Được sử dụng để gỡ bỏ(umount) file system. Có thể chỉ định thiết bị(device), nhãn hay điểm gắn(mountpoint)

	+ Ví dụ

	```sh 
	umount /mnt/data 
	``` 
	+ Sẽ hủy gắn mount thư mục /mnt/data từ bất kỳ thiết bị nào đã được gắn mount tại đó       
 
- Lưu ý: một filesystem chỉ có thể được hủy gắn mount nếu nó không được sử dụng

- `-f`: cố gắng hủy gắn mount filesystems một cách bắt buộc (ngay cả khi nó đang được sử dụng hoặc có các files đang mở)

- `fuser`: Nếu umount cho biết một filesystem đang được sử dụng, lệnh này sẽ cho bạn biết người dùng nào đang sử dụng nó  

- `-m [mount]`: xác định người đang sử dụng điểm gắn kết(mount point) được chỉ định  
 
	+ Ví dụ
	
	```sh
	fuser -m /mnt/data
	```  
	+ Sẽ hiển thị điểm gắn kết (mount points)và bất kỳ PID nào đang sử dụng nó cùng với chữ cái 'c' nếu nó được sử dụng làm thư mục hiện tại 
	(nói cách khác, một người dùng đang 'trong' thư mục)

### `/etc/fstab` 

- File định nghĩa bảng file system. Cấu hình mount(gắn) tạm thời được đặt ở đây. 

- Cấu hình mount trên một dòng duy nhất cho các filesystems local (và từ xa) sẽ được gắn mount khi khởi động Linux 

- Nội dung của các cột là:

	+ Cột 1. Thiết bị (ví dụ: /dev/sda1 HOẶC LABEL=data HOẶC UUID=44d27f92d3df-4207-80ea-22830afccf03) 
	
	+ Cột 2. Điểm gắn mount (ví dụ: / HOẶC /mnt/data, v.v.) 
	
	+ Cột 3. `Filesystem`: loại filesystem được hỗ trợ (ví dụ: ext3 HOẶC xfs, v.v.)

	+ Cột 4. `Tùy chọn`: danh sách phân tách bằng dấu phẩy  
    
		+ `noauto`: không tự động gắn mount khi khởi động (ngăn không cho các thiết bị ổ đĩa(External HDD) cắm ngoài được mount khi boot, do có thể gây ra vấn đề truy cập khi khởi động)

		+ `defaults`: tùy chọn ổ đĩa thông thường gồm rw, setuid, dev, exec, auto, nouser, async  
		
		+ `user`: chỉ người dùng gắn mount ổ đĩa (CD-ROM/DVD/Ổ đĩa External HDD) có thể gỡ bỏ nó  
		
		+ `users`: bất kỳ người dùng nào cũng có thể gỡ bỏ ổ đĩa (CD-ROM/DVD/Ổ đĩa External HDD)  
		
		+ `ro`: gắn mount chỉ cho phép đọc

	+ Cột 5. `dump`: giá trị '0' sẽ ngăn lệnh 'dump' ảnh hưởng đến ổ đĩa 
	
	+ Cột 6. `fsck`: giá trị '1' sẽ cho biết filesystem cần được kiểm tra đầu tiên  
          
- Lưu ý: `/etc/fstab` được sử dụng cho TẤT CẢ các loại mounts, cả mount local và từ xa.

