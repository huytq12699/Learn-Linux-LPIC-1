# Kiểm tra, sửa, xử lý lỗi cơ bản trong mạng

### ping

- Công cụ để kiểm tra phản hồi từ một địa chỉ mạng cụ thể.  

- `-n [#]`: Ping một số lần chỉ định

### netstat

- Có thể hiển thị kết nối mạng, bảng định tuyến, thống kê card mạng, vv.  

- `-a`: Hiển thị tất cả các socket trên giao diện mạng đang hoạt động  

- `-c`: Làm mới thống kê mỗi 1 giây  

- `-p`: Hiển thị tên và PID cho mỗi socket  

- `-t`: Hiển thị thống kê TCP 

- `-r`: Hiển thị bảng định tuyến  

- `-n`: Không phân giải tên (chỉ hiển thị IP)

### traceroute (chỉ có root có quyền chạy lệnh này)

- Công cụ để xác định khoảng cách (theo số bước nhảy) giữa hệ thống của bạn và điểm cuối mong muốn, cũng như thời gian phản hồi của mỗi bước trên đường đi.

- `-n`: Không phân giải tên cho mỗi bước nhảy, chỉ hiển thị IP.

### traceroute6  

- Tương đương IPv6 của traceroute. 

### tracepath (tất cả người dùng)  

- Công cụ để xác định khoảng cách (theo số bước nhảy) giữa hệ thống của bạn và điểm cuối mong muốn, cũng như thời gian phản hồi của mỗi bước trên đường đi.  

- `-n`: Không phân giải tên cho mỗi bước nhảy, chỉ hiển thị IP. 

### tracepath6  

- Tương đương IPv6 của tracepath 

### ping6  

- Lệnh ping cho IPv6 