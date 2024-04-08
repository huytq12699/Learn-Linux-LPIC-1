# Thiết lập bảo mật máy chủ

## Quản lý dịch vụ  

- Xác định cách/khi nào một dịch vụ(service) đang chạy (luôn chạy, chạy theo yêu cầu hoặc bị vô hiệu hóa(disabled)) 

## inetd  

- Tiến trình/dịch vụ cũ dùng để cung cấp các dịch vụ hệ thống "theo yêu cầu" hoặc khi cần thiết 

- `/etc/inetd.conf`: File cấu hình chính chứa một dòng duy nhất cho mỗi kiểm soát dịch vụ 

- Ví dụ:

```sh
telnet stream tcp nowait root /usr/sbin/in.telnetd in.telnetd
```  
   + Cấu hình mẫu cho telnet, theo thứ tự các trường sau:  
        
        + Tên dịch vụ: Tên của dịch vụ cần kiểm soát (ở ví dụ trên là `telnet`) 
        
        + Loại socket: Các giá trị có thể là stream, dgram, rdm, seqpacket (ở ví dụ trên là `stream`)  
        
        + Giao thức: File /etc/protocols xác định các giá trị, thông thường là TCP hoặc UDP (ở ví dụ trên là `tcp`)

        + Wait/nowait: Chờ cho các dịch vụ đơn luồng, nowait cho các dịch vụ đa luồng (ở ví dụ trên là `nowait`)

        + Người dùng(user)/nhóm(group): Nhóm hoặc tài khoản người dùng mà dịch vụ sẽ chạy dưới dạng (ở ví dụ trên là `root`)

        + Đường dẫn đến lệnh: Đường dẫn đầy đủ đến ứng dụng/dịch vụ để chạy (ở ví dụ trên là `/usr/sbin/in.telnetd`)

        + Đối số: Bất cứ điều gì có thể được yêu cầu để hoàn thành cấu hình dịch vụ (ở ví dụ trên là `in.telnetd`)

### xinetd

- Thay thế cho inetd để cho phép kiểm soát dịch vụ một cách chi tiết hơn

- `/etc/xinetd.conf`: File cấu hình chính, bao gồm các files trong `/etc/xinetd.d` với mỗi dịch vụ được kiểm soát  
    
    + Yêu cầu sẽ đi tới daemon, nó sẽ kiểm tra loại dịch vụ và cổng, sau đó quét file cấu hình dịch vụ thích hợp trong `/etc/xinit.d`  
    
    + Các trường quan trọng:  
        
        + `cps = [#] [#]`: Số đầu tiên giới hạn số kết nối mỗi giây đến dịch vụ, số thứ hai là độ trễ trước khi trả lời cho phép thêm kết nối  
        
        + `instances = [#]`: Tổng số tiến trình daemon được phép chạy cùng lúc 

### Các dịch vụ thường  

- finger, imap, rsh/rsync, telnet  

- File mẫu rsync từ /etc/xinet.d  

```sh
service telnet  
{  
   flags = REUSE  
   socket_type = stream  
   wait = no  
   user = root  
   server = /usr/sbin/in.telnetd  
   log_on_failure += USERID  
   disable = no  
}
``` 

### TCP wrappers

- Đối với `inetd`, chỉ sử dụng `/etc/hosts.allow` và `/etc/hosts.deny` như là các tham số của tcpd 

- Đối với `xinetd`, thư viện libwrap.a cho phép các dịch vụ sử dụng `/etc/hosts.allow` và `/etc/hosts.deny`

- Ví dụ (định dạng của mỗi dòng):

```sh
[service/daemon]: [host(s)]: [option]: [option] in.telnetd: 10.1.10.0/24
``` 
 
   + Cho phép (hoặc từ chối) người dùng trong mạng 10.1.10.0/24 truy cập vào dịch vụ telnet (phụ thuộc vào file nơi nó tồn tại)  

- Các phương pháp sử dụng để định nghĩa các chính sách:  
	
	+ Từ chối mặc định: Từ chối tất cả các máy truy cập đến tất cả các dịch vụ (ALL:ALL)  
       	
       	+ Sử dụng như một phần dự phòng trong `hosts.deny` vì các kết quả khớp trong `hosts.allow` sẽ ghi đè lên.  
    
    + Cho phép mặc định: Tự động tin tưởng tất cả mọi người và cung cấp quyền truy cập đến tất cả mọi thứ  
        	
        + Mối nguy hiểm về mặt bảo mật rõ ràng  
    
    + Kết hợp: Cho phép và từ chối theo cách lựa chọn 

### Thứ tự ưu tiên cho hosts.allow và hosts.deny

- `hosts.allow` được đọc trước, nếu khớp với các dòng cấu hình trong file thì được cho phép và `hosts.deny` được bỏ qua (hoàn toàn).  

	+ Thay đổi trong `hosts.allow/deny` có hiệu lực ngay sau khi thay đổi file.  

- Đọc tuần tự: Có nhiều mục nhập cho cùng một dịch vụ sẽ chỉ áp dụng mục nhập đầu tiên.    

- Nếu các files không tồn tại, không có quy tắc nào được áp dụng. 

- Có thể thêm các tùy chọn khác thay vì chỉ từ chối dịch vụ.  
      
    + Ví dụ:
     
      	```sh
      	in.telnetd: 10.1.10.0/24 : twist /bin/echo "Service 404 - Service Not Found"  
      	```