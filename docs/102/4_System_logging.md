# System Logging

### syslog (có thể là rsyslog, klogd)  

• Giao thức đơn giản để ghi nhật ký(log) thông điệp hệ thống

• Các ứng dụng có thể truy cập vào syslog thông qua lệnh thư viện syslog hoặc qua tiện ích dòng lệnh logger  

• Daemon (syslogd) sẽ xử lý các thông điệp, các cấp độ ghi nhật ký có thể là:        
   
   • 0: Khẩn cấp (Emergency) 
   
   • 1: Cảnh báo (Alert) 
   
   • 2: Nghiêm trọng (Critical) 
   
   • 3: Lỗi (Error) 
   
   • 4: Cảnh báo (Warning) 
   
   • 5: Thông báo (Notice) 
   
   • 6: Thông tin (Info) 
   
   • 7: Gỡ lỗi (Debug)  

• Ghi nhật ký ở một cấp độ cụ thể sẽ giới hạn thông điệp được ghi nhật ký ở cấp độ đó hoặc cao hơn (cấp độ ghi nhật ký 3 có nghĩa là sự kiện 0, 1, 2, 3 được ghi nhật ký trong khi các sự kiện 4 và thấp hơn bị bỏ qua)

### rsyslog  
 
• Phiên bản "nhanh" thay thế của syslog

### syslog-ng

• Phiên bản "thế hệ tiếp theo" thay thế của syslog

### "facilities" ghi nhật ký

• Ghi nhật ký cụ thể được liên kết với các mục khác nhau (mô tả những gì được ghi nhật ký)  
   
   • kern: Các thông điệp kernel (Kernel messages) 
   
   • user: Các thông điệp cấp người dùng (User level messages) 
   
   • mail: Máy chủ email (Mail server) 
   
   • daemon: Dịch vụ/daemon (Services/daemons) 
   
   • auth: Nhật ký bảo mật (public) (Security logs) 
   
   • syslong: Các thông điệp syslog nội bộ (Internal syslog messages) 
   
   • lpr: In ấn (Printing) 
   
   • cron: Lập lịch công việc (Job scheduling) 
   
   • authpriv: Nhật ký bảo mật (riêng tư) (Security logs) 
   
   • local0-7: Định nghĩa bởi người dùng (có sẵn 8 cái khác nhau)( User definable)

### /var/log/message

• Nơi chứa tất cả các thông điệp nhật ký (trừ mail)

### /var/log/maillog

• Các thông điệp emails được ghi vào đây

### logger

• Cho phép bạn sử dụng một lệnh ghi một thông điệp vào /var/log/messages  

• Nhấn CTL+D để kết thúc và ghi tin nhắn  

• -i: Chuyển thông tin bổ sung đến syslog 

### /etc/syslog.conf

• file cấu hình syslog  

• Xác định nơi các facilities cụ thể sẽ ghi nhật ký

### systemd

• Sử dụng hệ thống ghi nhật ký riêng gọi là journal (với journald là daemon cho nó)  

• Được áp dụng trên hầu hết các bản phân phối Linux dựa trên systemd hiện đại 

• Chủ yếu, khác biệt nằm ở việc ghi nhật ký được thực hiện vào một file nhị phân chứ  không phải file văn bản thuần túy, cho phép bạn truy vấn dữ liệu siêu dữ liệu, chi tiết dòng lệnh, PIDs, các files nhị phân và đặc quyền bảo mật (một số trong số đó không có sẵn trong file văn bản thuần)  

• Bới vì nó là một phần của hệ thống quản lý dịch vụ trong Linux, tất cả các thông điệp của daemon được tự động ghi nhật ký thay vì syslog phiên bản sysvinit trong đó mỗi dịch vụ chịu trách nhiệm về cách và những thông điệp nào được ghi vào nhật ký

### /var/log/journal  

• file nơi lưu trữ thông tin ghi nhật ký của systemd

### journalctl

• Lệnh được sử dụng để xem file nhật ký journal đã đề cập trên console: 
   
   •  -f: Cho phép bạn theo dõi khi có các thông điệp nhật ký mới được ghi  
   
   •  SYSLOG_IDENTIFIER=[giá trị]: Cho phép bạn thêm bộ lọc để chỉ hiển thị các mục nhật ký phù hợp với tiêu chí  
   
   •  -u [dịch vụ]: Chỉ hiển thị các thông điệp được ghi nhật ký từ dịch vụ được chỉ định  
   
   •  -o verbose: Hiển thị nhiều thông tin hơn về dịch vụ hoặc bộ lọc được yêu cầu  
   
   •  -e: Di chuyển đến cuối nhật ký  
   
   •  -x: Thêm thông tin để giải thích ngữ cảnh trong đó một sự kiện hoặc lỗi được ghi nhật ký xảy ra (như trong trường hợp lỗi khởi động dịch vụ)

### /etc/systemd/journald.conf  

• File cấu hình cho journald

• Các thiết lập thông thường cho kích thước nhật ký và xem xét việc chuyển tiếp ghi nhật ký đến syslog cũng như tương đương đã được cài đặt.

### Log rotation(xoay vòng nhật ký)

• Định kỳ sao lưu, nén và/hoặc xóa các files nhật ký đáp ứng tiêu chí nhất định để quản lý không gian đĩa và hiệu suất I/O.  

• /etc/logrotate.conf (và bất kỳ thứ gì trong /etc/logrotate.d)  

• Cấu hình chính cho việc xoay vòng nhật ký (cài đặt mặc định và file hệ thống để xoay  vòng)  

• Mỗi file trong logrotate.d thêm hoặc ghi đè các thiết lập lên cài đặt mặc định trong file cấu hình

• Các files đang mở trong quá trình xoay vòng nhật ký được xử lý theo một trong 3 cách:  

   •  Di chuyển nhật ký, tạo tín hiệu đóng file và mở lại nhật ký; không phải ứng dụng nào cũng hỗ trợ phương pháp này  
   
   •  Khởi động lại ứng dụng/dịch vụ sau khi di chuyển file nhật ký, nhật ký sẽ bắt đầu ghi vào một file mới "trống"; có thể gây vấn đề nếu khởi động lại dịch vụ ảnh hưởng đến người dùng hoặc kết nối  
   
   •  Sao chép nhật ký và sau đó cắt ngắn nhật ký hiện tại ngay tại chỗ; tốn kém về hiệu suất ổ đĩa và các mục nhập nhật ký có thể bị mất trong quá trình giao dịch 