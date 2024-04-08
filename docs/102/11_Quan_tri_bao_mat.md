# Quản trị Bảo mật 

### root  

- Tài khoản quản trị hệ thống.  

- Thực hành bảo mật tốt nhất là không đăng nhập trực tiếp vào hệ thống với quyền root, mà là "trở thành" root.  

- Hai phương pháp: 

	+ `su`: Nhập mật khẩu root và sau đó trở thành root (su = superuser) 

	+ `sudo su`: Nhập mật khẩu của bạn, miễn là bạn có đặc quyền sudo (sudo = superuser do), sau đó bạn sẽ trở thành root. 

### su 

- Super user

    + Ví dụ: su root 
        
       	+ Trở thành người dùng root, nhưng các kịch bản shell đăng nhập của user root (.bash_login, .bashrc, vv.) sẽ không được thực thi, vì vậy bạn sẽ không thừa hưởng các giá trị của môi trường shell của user root. 
           	
           	+ Ví dụ: `su - root`  
                
                + Trở thành root và tất cả các kịch bản shell đăng nhập sẽ được thực thi và môi trường và cài đặt đầy đủ sẽ được sử dụng.  
                
                + Cũng có thể được thực hiện với `su -l root`

    + Áp dụng cho cả người dùng thường (miễn là bạn biết mật khẩu tương ứng)

    + Lưu ý: Root có thể `su` sang bất kỳ người dùng nào mà không cần phải biết mật khẩu của người dùng đó. 

### visudo  

- Chế độ chỉnh sửa đặc biệt cho VI cho phép chỉnh sửa và kiểm tra cú pháp/lỗi của file `/etc/sudoers` 

- Lưu ý: Trình soạn thảo này được sử dụng có thể được thay đổi bằng cách đặt biến môi trường EDITOR thành bất kỳ trình chỉnh sửa văn bản khác có sẵn

### /etc/sudoers  

- File liệt kê người dùng có thể thực thi các lệnh với đặc quyền root.  

- Định dạng yêu cầu người dùng được liệt kê (hoặc một nhóm nếu toàn bộ nhóm đó phải có đặc quyền root) cùng với các quyền của họ trong Linux  
    
    + Ví dụ: `user ALL=(ALL) ALL`  
          	
          	+ Sẽ cung cấp quyền sudo cho tài khoản người dùng cho tất cả các lệnh được sử dụng với đặc quyền root  
    
    + Ví dụ: `user ALL=(ALL) /bin/systemctl`  
            
            + Sẽ giới hạn người dùng chỉ có thể chạy systemctl với đặc quyền sudo (để có thể khởi động lại các dịch vụ services) 

### find 

- Ngoài các lệnh thường để tìm kiếm các files, thư mục, v.v., có thể sử dụng để tìm kiếm các files có các quyền cụ thể hoặc do người dùng cụ thể sở hữu.  

- Được sử dụng để khôi phục từ việc thay đổi quyền do sơ suất (hoặc độc hại)  

- `-user [user]`: Tìm các files thuộc sở hữu của người dùng được chỉ định  

- `-perm [permissions]`: Tìm các files có các quyền được chỉ định  
    
    + Có thể bao gồm các quyền "bit đặc biệt"  
    
    + `+`: Tìm bất cứ thứ gì phù hợp với số đầu tiên  
    
    + `-`: Tìm kiếm chính xác khớp cho số đầu tiên

- `-type [type]`: Tìm kiếm các files, liên kết, thiết bị, thư mục
 
- `-exec [commands] {} ;`: Thực hiện các lệnh đã chỉ định trên các files được tìm thấy 
                   • Ví dụ: find / -user root -perm 0777 -type f -exec ls -al {} ; | mail -s "Files owned by  
                      root with world rwx permissions" root  
                        • Lệnh trên sẽ tìm kiếm tất cả các files thuộc sở hữu của người dùng root với tất    
                          cả các quyền đọc/ghi/thực thi mà cho phép tất cả các người dùng có thể thực thi ,  
                          sau đó gửi email danh sách đó với danh sách hiển thị của tất cả các files cho  
                          người dùng root với chủ đề(subject) được chỉ định

### Các mục khác có thể được sử dụng để điều tra/bảo mật hệ thống

- passwd, fuser, lsof, chage, usermod, ulimit, w, /etc/inittab 