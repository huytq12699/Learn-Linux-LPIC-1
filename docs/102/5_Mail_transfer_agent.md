# Dịch vụ gửi và nhận Mail

## Máy chủ mail  

- Sendmail  
      
   + Máy chủ mail kiểu cũ, có thể là "tiêu chuẩn" mà các bản phân phối Linux sẽ cài đặt. Có điểm yếu dễ bị tấn công bảo mật và được biết đến là khó cấu hình.  

- Postfix  

   + Ban đầu được phát triển bởi IBM, đã thay thế Sendmail như máy chủ thư mặc định trên  các bản phân phối Linux hiện đại. Tích hợp hỗ trợ các luật để giảm thư rác và phân tách các tiến trình vì mục đích bảo mật.  

- Qmail  
	
	+ Là một sự thay thế an toàn cho Sendmail. Các tiến trình riêng biệt cho phép cải thiện bảo mật và cô lập và cấu hình đơn giản hơn, các cải thiện này giúp Qmail trở thành một sự lựa chọn tốt. Tuy nhiên, gần đây việc phát triển nó đã kém hơn.  

- Exim  

	+ Giống như Sendmail với tính chất và cấu hình "monolithic" hơn, mặc dù nó được biết đến với lịch sử bảo mật tốt hơn. Cấu hình đơn giản hơn và đôi khi được coi là máy chủ mail mặc định trong các phiên bản cũ của bản phân phối Debian.

## SMTP

- Simple Mail Transfer Protocol: Đây là một giao thức định nghĩa cách emails được chuyển tiếp và lưu trữ và là một phần của tầng ứng dụng TCP/IP cũng như các quy tắc cấu hình mà các ứng dụng emails tuân thủ theo. 

## MUA

- Mail User Agent: Đây là các ứng dụng nào bạn sử dụng để soạn và gửi email (Thunderbolt, Evolution, SquirrelMail, v.v.).

## MSA

- Mail Submission Agent: Hoạt động như một trung gian hoặc cổng thông tin giữa MUA và MTA để bắt đầu quá trình chuyển tiếp email. 

## MTA

- Mail Transfer Agent: Nhận emails từ MUA và gửi nó (nếu cần) đến máy chủ mail đích (MTA khác nếu đây không phải là đích). Có nhiều máy chủ MTA trong Linux (Postfix, mà chúng ta sẽ sử dụng, Sendmail và nhiều loại máy chủ mail khác). 

## MDA  

- Mail Delivery Agent: Nhận email từ MTA và sau đó chuyển nó đến mail spool cục bộ để người dùng có thể lấy emails về bằng các loại ứng dụng thư điện tử. Đôi khi MTA cũng có thể hoạt động như MDA, nhưng (ví dụ như procmail)  chúng là các ứng dụng độc lập cũng có thể dùng thể lọc emails (như chống spam). 

## POP

- Post Office Protocol: Được MUAs sử dụng bởi để lấy email (sẽ được đề cập chi tiết hơn sau). 

## IMAP

- Internet Message Access Protocol: Được MUAs  sử dụng để lấy email (sẽ được đề cập chi tiết hơn sau). 

## MX Record 

- Đây là các bản ghi DNS mail. Các bản ghi này được sử dụng bởi MTAs để xác định máy chủ mail có thẩm quyền cho bất kỳ email nào.

## Mail Transfer Agent (MTA) Basics (Tạo bí danh)
 
### /etc/aliases  

- Cho phép gọi một người dùng bằng tên/khác

    + Ví dụ (ghi trong file): sysadmin: root  
        + Sẽ chỉ ra là nếu một email được gửi đến máy chủ mail cho tài khoản sysadmin sẽ được chuyển tới root

- Định dạng của một bí danh (alias): alias: account[,another,another] 
       	+ Dấu ngoặc vuông là tùy chọn, xác định danh sách các tài khoản mà một bí danh đề cập đến là một danh sách được phân cách bằng dấu phẩy

- Lưu ý: Một bí danh có thể là bất kỳ tên nào, có thể được sử dụng để gửi email của một tài khoản tới một tài khoản khác  
       	+ Ví dụ: root: user,user1
			+ Gửi email của root tới user và user1

- Cũng có thể chấp nhận địa chỉ email là một tài khoản để gửi mail nội bộ (nếu máy chủ mail được cấu hình)  
        + Ví dụ: sysadmin: user@abc.com  
           	+ Sẽ gửi email của sysadmin tới địa chỉ user@abc.com 

- Email cũng có thể được gửi tới một file từ một bí danh  
        + Ví dụ: sysadmin: /root/sysadmin.email  
            + Sẽ gửi tất cả email tới file sysadmin.email trong thư mục của root user  

- Có thể gửi tới một kịch bản/ứng dụng  
        + Ví dụ: support: | /opt/HelpDesk/create_ticket.sh  
            + Sẽ gửi email và gây lên việc thực thi một kịch bản (lưu ý kịch bản phải được tiền đề bằng ký tự ống |) 

### /etc/aliases.db

- file cơ sở dữ liệu mà MDA cục bộ của bạn sẽ đọc để xác định nơi gửi email; nó phải được cập nhật khi có bất kỳ thay đổi nào được thực hiện với bí danh trong Linux 

### newaliases

- Lệnh cập nhật aliases.db với các thay đổi trong file aliases ở trên  
    
- Sẽ hiển thị lỗi nếu có, thành công sẽ không trả về kết quả  

- Nếu bạn thay đổi aliases mà không chạy lệnh này, thông báo sẽ được ghi lại trong /var/log/messages là cơ sở dữ liệu cũ hơn file aliases 

### forward  

- file trong thư mục home cho người dùng để định nghĩa các quy tắc chuyển tiếp các emails riêng của họ 

- Không cần chỉ định bí danh, vì nó thuộc về tài khoản mà nó tồn tại trong; chỉ cần chỉ định tài khoản để chuyển tiếp emails tới 

### mailq  

- Lệnh hiển thị hàng đợi email 

### var/spool/mqueue  

- Các emails đang chờ được gửi đi 

- Chỉ tồn tại nếu có emails trong hàng đợi; trên một máy chủ được cấu hình đúng, nó nên là trống 

### /var/log/maillog

- Ghi lại tất cả các thông điệp thư điện tử khi chúng đi vào và ra khỏi Linux   