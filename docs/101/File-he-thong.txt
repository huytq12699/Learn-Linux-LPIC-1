* # File hệ thống*
- Hệ thống tập tin của Linux được tổ chức theo 1 hệ thống phân bậc tương tự cấu trúc của 1 cây phân cấp. Bậc cao nhất là thư mục gốc, ký hiệu là "/" (root directory)

- `/bin` - User binaries và `sbin` - System binaries
	+ Chứa những file cần thiết cho quá trình khởi động và những lệnh thiết yếu để duy trì hệ thống
- `/dev` - Files device
	+ Chứa các định danh ánh xạ của thiết bị hoặc những file đặc biệt 
- `/etc` - Configuration Files
	+ Chứa các file cấu hình của hệ thống và nhiều chương trình tiện ích
- `/lib` - System Libraries
	+ Chứa các thư viện dùng chung cho các lệnh nằm trong `/bin` và `/sbin`. Và thư mục này cũng chứa các module của nhân.
- `/mnt` - Mount Directory
	+ Mount point mặc định cho những hệ thống file kết nối ra ngoài
- `/proc` - Mount Directory
	+ Chứa các thông tin về tiến trình hệ thống
- `/boot` - Boot Loader Files
	+ Chứa tập tin cấu hình cho quá trình khởi động của hệ thống
- `/home` - Thư mục Home
	+ Thư mục mặc dành cho người dùng khác root. Lưu trữ các tập tin cá nhân của tất cả user
- `/root` - Thư mục Root
	+ Thư mục mặc định của người dùng root
- `/tmp` - Temporary Files
	+ Thư mục chứa các file tạm thời
- `/usr` - User Programs
	+ Thư mục chứa những file cố định hoặc quan trọng để phục vụ tất cả người dùng
	+ Chứa các ứng dụng, thư viện, tài liệu và mã nguồn các chương trình thứ cấp
- `/var`
	+ Thư mục chứa các tập tin ghi các số liệu biến đổi
	+ Bao gồm: Hệ thống tập tin log `/var/log`, các gói và các file dữ liệu `/var/lib`, email `/var/mail`, print queues `/var/spool`, lock files `/var/lock`, các file tạm thời cần khi reboot `/var/tmp`
- `/media` - Removable Media Devices
	+ Gắn kết các thư mục tạm thời được hệ thống tạo ra khi một thiết bị lưu động (removable media)
- `/srv` - Service Data
	+ Chứa các service của máy chủ cụ thể liên quan đến dữ liệu

## Hệ thống tập tin

Hệ thống linux gốc 'ext3', 'ext4', 'btrfs', 'xfs'. Trước khi sử dụng 1 hệ thống tập tin, phải gắn nó vào cây hệ thống tại `mountpoint`. Nên gắn vào thư mục trống.
- `mount`: Sử dụng để gắn vào cây tập tin
```sh
mount /dev/sd5a /mnt
```

> Đính kèm hệ thống tập tin có trong phân vùng đĩa được liên kết với dev/sd5a trên thiết bị vào cây tệp tin tại /mnt

- `unmount`: Tác các hệ thống tập tin từ điểm gắn
```sh
unmount /mnt
```