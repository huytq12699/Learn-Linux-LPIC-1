# Cấu hình mạng cơ bản

### nmcli

- công cụ giao diện dòng lệnh cho NetworkManager  

- `dev`: Hiển thị thông tin thiết bị (liên quan đến phần cứng mạng)  

- `con`: Hiển thị thông tin cấu hình kết nối

### ifconfig 
 
- Công cụ để xem tất cả các card mạng hoạt động (bao gồm cả card loopback)  

- `-a`: Hiển thị TẤT CẢ các card mạng (hoạt động hoặc không hoạt động)  

- Các trường quan trọng:

   	+ `ether`: Địa chỉ phần cứng (MAC), địa chỉ vật lý của card mạng 48 bit  
    
   	+ `inet`: Địa chỉ mạng được gán cho card mạng đó  
    
    + `broadcast`: Địa chỉ broadcast (phát sóng) cho mạng của hệ thống  
    
    + `netmask`: Mặt nạ mạng hoặc thông tin đoạn mạng logic  

- Lưu ý: Đây là một lệnh mạng cổ điển đang bị thay thế bằng lệnh thế hệ mới

### ifup

- Kích hoạt giao diện mạng (card mạng) được chỉ định

### ifdown

- Tắt giao diện mạng (card mạng) được chỉ định 

### ip  

- Lệnh quản lý mạng và định tuyến thống nhất được thiết kế để thay thế chức năng của hầu 
hết các lệnh khác. 

- Ví dụ: `ip addr show`  
   
   + Sẽ cung cấp cho bạn thông tin tương tự như lệnh ifconfig ở trên 

### File cấu hình card mạng 

- Red Hat/CentOS (v6)  

	+  `/etc/sysconfig/network-scripts` 
           
    + Một thư mục chứa các tập lệnh chịu trách nhiệm cấu hình tất cả các interfaces trên hệ thống  
            
       	+ Ví dụ: `ifcfg-eth1`  
                
            + Chịu trách nhiệm cho cấu hình (IP tĩnh hoặc DHCP) thông tin địa chỉ cho interface ETH1 trên hệ thống Linux của bạn  
	
	+ Thay đổi cấu hình giao diện mạng được áp dụng bằng cách khởi động lại dịch vụ mạng 
            
        + Ví dụ:

        ```sh
        service network restart  
        ```

- Debian/Ubuntu

    + `/etc/network/interfaces`  
    
    + Được cấu hình bằng `system-config-networking` hoặc `netcardconfig` 
    
    + Thay đổi cấu hình giao diện mạng được áp dụng bằng cách khởi động lại dịch vụ networking  
        
        + Ví dụ: 

        ```sh
        /etc/init.d/networking restart 
        ```

### Default gateway(Cổng mặc định)

- Đích của TẤT CẢ lưu lượng mạng có đích không nằm trong mạng hệ thống mạng cục bộ 
HOẶC không có một static route định tuyến tĩnh phù hợp khác được cấu hình.

- Có thể được cấu hình trong `/etc/sysconfig/network` hoặc `/etc/sysconfig/network-scripts/ifcfg-eth0` (trong đó # là số giao diện)  
             
- Ví dụ: `GATEWAY=192.168.1.1` 
           
    + Sẽ cấu hình Default GW của Linux với địa chỉ IP 192.168.1.1 

### Route  

- Hiển thị bảng định tuyến(routing table) hiện tại  

- Thêm/xóa định tuyến theo yêu cầu  
 	
 	+ Ví dụ: `route add default gw 192.168.1.1`  
            
        + Sẽ thêm một Default GW vào hệ thống đi đến 192.168.1.1  
    
    + Ví dụ: `route add 192.168.10.211 lo`
      
        + Sẽ định tuyến tất cả lưu lượng(traffic) trả về cho loopback adapter (giải pháp nhanh chóng chống lại một cuộc tấn công mạng DoS attack từ một địa chỉ IP duy nhất, trường hợp này IP là: 192.168.10.211)

- `add`: Thêm một gateway/route/destination 

- `default`: Từ khóa để thêm/xóa một Default GW  

- `gw`: Viết tắt của gateway, tất cả lưu lượng không khớp với các quy tắc khác được định tuyến đến đây  

### IP forwarding  

- Khả năng cho phép máy chủ của bạn chuyển tiếp gói tin đến vị trí khác và phản hồi  

- Cho phép Linux của bạn hoạt động như một bộ định tuyến router 
   
- Có 2 phương pháp để kích hoạt: 
 
    + pp1: 

    ```sh
    echo 1 > /proc/sys/net/ipv4/ip_forward 
    ```  
    + pp2: sửa `/etc/sysctl.conf` và thêm `net.ipv4.ip_forward=1`  
        
    + Lưu ý: Phương pháp 1 không phải là vĩnh viễn nhưng sẽ có hiệu lực ngay lập tức, phương pháp 2 yêu cầu khởi động lại (hoặc kết hợp với phương pháp một) 

### Gia hạn địa chỉ DHCP lease

- `dhcpd -k`: Dừng và khởi động lại tiến trình để nhận địa chỉ IP mới  
 
- `dhclient`: Sau khi khởi động lại dịch vụ mạng (network services), chạy để nhận địa chỉ IP mới  

- `pump`: Công cụ cũ, dùng để nhận một địa chỉ DHCP mới

### hostnamectl  

- Lệnh được sử dụng để cấu hình tên máy cục bộ một cách vĩnh viễn 