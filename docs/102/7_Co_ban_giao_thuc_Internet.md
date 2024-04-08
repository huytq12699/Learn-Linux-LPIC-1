# Giao thức Internet

### IP (Internet Protocol)

- Một phương pháp xác định duy nhất địa chỉ (đích) cho một hệ thống cụ thể. Có 2 phiên bản chính: 
    
   	+ IPv4: Cấu trúc địa chỉ tiêu chuẩn gồm bốn "octet" chứa các số từ 0-255 cho mỗi octet (ví dụ: 192.168.72.211). 
    
   	+ IPv6: Được thiết kế để thay thế IPv4, gồm một số thập lục phân 128 bit cho địa chỉ (ví dụ: 2DAF:FF40:0928:CD01:4433:00DD:0988:FFFF). 

### TCP (Transmission Control Protocol) 

- Phương pháp mà tất cả các giao dịch giữa các địa chỉ IP (bất kỳ phiên bản nào) được truyền thông. 

- Định nghĩa một hệ thống truyền và xác nhận để đảm bảo lưu lượng dữ liệu đến và có thể được lắp ráp theo đúng thứ tự. 

### UDP (User Datagram Protocol)

- Thường được coi là "bổ sung" cho IP, nhưng là một kết nối "không lưu trạng thái".  
              
- Không có kiểm tra lỗi hoặc gửi lại các gói tin, ngay cả khi gửi gói tin không thành công.

### ICMP (Internet Control Message Protocol)  

- Được thiết kế cho các thiết bị mạng (bộ định tuyến(routers), switch thông minh, tường lửa(firewall), vv.) để gửi các thông báo lỗi. 

- Ngoài ra, nó cũng có thể thực hiện các truy vấn sẵn có của dịch vụ mạng (như trong trường hợp sử dụng lệnh ping để kiểm tra xem một địa chỉ có đáp ứng yêu cầu hay không).

### Phạm vi Lớp IP 

- RFC 1918 chỉ định năm phạm vi. Các giá trị trong mỗi phạm vi xác định tổng số lượng các hosts trong mỗi lớp (địa chỉ):  
       
   	+ `Lớp A: Từ 1 đến 126`   - có 16.777.214 địa chỉ hosts

   	+ `Lớp B: Từ 128 đến 191` - có 65.534 địa chỉ hosts 

   	+ `Lớp C: Từ 192 đến 223` - có 254 địa chỉ hosts

   	+ `Lớp D: Từ 224 đến 239` - dùng cho multicast và không sử dụng cho địa chỉ hosts 
       
   	+ `Lớp E: Từ 240 đến 254` - dành cho việc sử dụng trong tương lai

### Mặt nạ mạng(Network Mask)

- Định nghĩa một mạng logic (gọi là mạng con subnet) chỉ ra điểm bắt đầu và kết thúc của một dải địa chỉ. 

### Phạm vi  

- Mỗi phạm vi lớp địa chỉ có một mặt nạ mạng/mạng con tương ứng.  

- Số bit (được chỉ định bởi /) được gọi là ký hiệu Ghi chú địa chỉ mạng (CIDR).  
   
    + Lớp A: 255.0.0.0 (hoặc /8)  
    
    + Lớp B: 255.255.0.0 (hoặc /16)  
   
    + Lớp C: 255.255.255.0 (hoặc /24) 

### Cổng mạng (Gateway)  

- Được sử dụng để kết nối mạng cục bộ với mạng bên ngoài, chẳng hạn như kết nối mạng nội bộ với Internet. 

- Gateway có vai trò chuyển tiếp gói tin giữa các mạng khác nhau và thực hiện chức năng định tuyến để định địa chỉ đích của gói tin. 

### Địa chỉ Broadcast (phát sóng) 

- Địa chỉ Broadcast  

- Mỗi mạng đều có một địa chỉ Broadcast, hoạt động trên số địa chỉ là 255.  
   
   	+ Ví dụ: Mạng 192.168.1.0/24

          	+ 192.168.1.255 là địa chỉ Broadcast

           	+ Đây là cách mà một mạng IP gửi lưu lượng mà có thể được nhìn thấy bởi tất cả các máy trên mạng.

### Cổng/Dịch vụ phổ biến

• 20/21: FTP

• 22: SSH

• 23: Telnet

• 25: SMTP

• 53: DNS

• 80: HTTP

• 110: POP3

• 123: NTP

• 139: NETBIOS

• 143: IMAP

• 161/162: SNMP

• 389: LDAP 

• 443: HTTPS

• 465: SMTPS

• 514: SYSLOG

• 636: LDAPS

• 993: IMAPS 

• 995: POP3S