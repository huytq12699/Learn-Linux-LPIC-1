# Cấu hình DNS phía máy khách

1. `/etc/hosts`

- File cục bộ chứa tên liên kết với một địa chỉ IP 

2. `/etc/resolv.conf`  

- Xác định máy chủ DNS và tên miền của hệ thống để phân giải tên miền. 

3. `/etc/nsswitch.conf`  

- Xác định thứ tự các truy vấn phân giải tên cục bộ so với truy vấn phân giải tên miền từ xa.      
   
   	+ Ví dụ: `hosts: files dns` 
       
       	+ Dòng cấu hình trên sẽ cho phép Linux kiểm tra `/etc/hosts` trước khi kiểm tra các máy chủ DNS có trong `/etc/resolv.conf` 


## Các lệnh sau đây yêu cầu gói bind-utils 

1. `Host` 

- Lấy thông tin DNS về máy chủ chỉ định (thực hiện các truy vấn DNS). 

2. `getent`  

- hosts [name]: Lấy thông tin về tên máy chủ chỉ định (sẽ đọc `/etc/nsswitch.conf` để xác định thứ tự tìm kiếm) 

3. `dig`

- [server] [domain] [loại bản ghi]: Tất cả tùy chọn trừ domain  

- server: Chỉ định một máy chủ DNS để sử dụng  

- domain: Miền cụ thể để truy vấn  

- record type: Các loại bản ghi khác nhau (ví dụ: NAME, CNAME, MX, vv.) 