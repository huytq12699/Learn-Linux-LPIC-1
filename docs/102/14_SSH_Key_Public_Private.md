# SSH Keys - Public và Private - cho Kết nối Bảo mật

1. ssh

- Secure Shell  
    
	+ Các lệnh liên quan (cũng bảo mật): scp, ssh-agent, ssh-add

- `-l [user] [host]`: Đăng nhập dưới tên người dùng được chỉ định vào máy chủ  

- `[user]@[host]`: Đăng nhập dưới tên người dùng được chỉ định vào máy chủ  

- `-X`: Bật chuyển tiếp SSH X Window System  

- `-x`: Tắt chuyển tiếp SSH X Window System 

2. `/etc/ssh/sshd_config`: Cấu hình chính cho sshd

3. `/etc/ssh/ssh_host_[rsa/dsa]_key`: Private keys mã hóa cụ thể với quyền 600 để hạn chế truy cập cho người dùng root

4. `/etc/ssh/ssh_host_[rsa/dsa]_key.pub`: Public keys mã hóa cụ thể với quyền 644 để hạn chế truy cập cho người dùng root và cấp quyền đọc cho người dùng khác 

5. `/etc/ssh/known_hosts` 

- file được sử dụng để kiểm tra public key của các máy chủ đã biết/đáng tin cậy (không tồn tại theo mặc định)

6. `~/.ssh/known_hosts`  

- file chứa public key của các máy chủ đã biết/đáng tin cậy đã kết nối tới/từ máy chủ hiện tại bởi người dùng sở hữu thư mục đó.

7. `~/.ssh/authorized_keys` 

- Lưu trữ public keys để đăng nhập dưới dạng người dùng sở hữu thư mục.

8. `ssh-keygen`  

- Tạo cặp khóa public/private để sử dụng với SSH.

- `-b [#]`: Kích cỡ key mã hóa (ví dụ: 1024, 2048, v.v.)  

- `-t [type]`: Loại key mã hóa (DSA hoặc RSA - RSA an toàn hơn và hiện tại là mặc định)

 	+ Sẽ yêu cầu mật khẩu - để trống sẽ cho phép bạn sử dụng khóa để đăng nhập hoàn toàn mà không cần mật khẩu, trong khi nhập một passphrase sẽ tạo ra xác thực hai yếu tố (khóa + passphrase)  
    
    + Quyền của file trên khóa nên là 644 (cũ) hoặc 600 (mới)

9. `ssh-copy-id`  

- Copy public key của bạn tới người dùng và máy chủ được chỉ định.  
    
    + Ví dụ: ssh-copy-id user@user.mylabserver.com  
        
        + Sau khi nhập mật khẩu cho người dùng đã chỉ định, nó sẽ sao chép public key từ máy chủ và người dùng này vào file authorized_keys của máy chủ từ xa và người dùng đó, và sau đó bạn có thể đăng nhập vào hệ thống và tài khoản đó bằng key này.

- Phương pháp thủ công: Sao chép/dán nội dung public key của bạn vào file authorized_keys của người dùng từ xa và đặt quyền truy cập là 600.

- Kết nối tiếp theo sẽ hoạt động (không cần đặt passphrase) hoặc yêu cầu chỉ cần passphrase.

10. `ssh-agent`  

- Bao bọc cho SSH cho phép bạn chuyển các mục (key) vào trong SSH shell để kết nối. 

- Thực hiện ssh-agent để khởi động agent trên shell được chỉ định  
    
    + Ví dụ: `ssh-agent bash`  
       
       +  Khởi động một dấu nhắc bash với agent bao bọc nó. 

11. `ssh-add`  

- Sẽ yêu cầu bạn cung cấp passphrase cho public key của bạn (nếu được thiết lập)  

- Sau khi nhập, việc sử dụng tiếp theo sẽ không đòi hỏi nhập lại cho đến khi thoát.
