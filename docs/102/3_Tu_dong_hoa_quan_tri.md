# Tự động hóa quản trị bằng cách lập lịch

## cron 

+ Là hệ thống lập lịch chính cho các công việc trong Linux.

+ Công việc được cấu hình để chạy theo lịch trình cố định (một lần hoặc nhiều lần tùy theo yêu cầu)

+ `crond`  
	• Dịch vụ chịu trách nhiệm đảm bảo là các công việc cron được chạy

+ `/etc/cron.*`
    • cron.d: Thư mục cấu hình lịch trình công việc tùy chỉnh (công việc cron hệ thống) 
    • cron.hourly: Các công việc chạy hàng giờ  
    • cron.daily: Các công việc chạy hàng ngày  
    • cron.weekly: Các công việc chạy hàng tuần 
    • cron.monthly: Các công việc chạy hàng tháng

+ Lưu ý: Trong các thư mục ngoại trừ cron.d, các thư mục này chỉ chứa các tập lệnh mà không bao gồm thông tin lập lịch khác và chúng sẽ không chạy vào cùng thời điểm, nhưng sẽ chạy trong khoảng thời gian được chỉ định. 

## crontab 

• Tiện ích cho phép tạo công việc (định nghĩa lập lịch riêng cho người dùng chạy lệnh) 
    • -l: Liệt kê tất cả các công việc cron cho người dùng đã đăng nhập  
    • -e: Chỉnh sửa các công việc cron cho người dùng đã đăng nhập  
    • -u [tên người dùng]: Áp dụng tùy chọn cho người dùng được chỉ định

##  Định dạng một mục công việc cron 

• [Phút 0-59] [Giờ 0-23] [Ngày trong tháng 1-31] [Tháng 1-12] [Ngày trong tuần 0-7] [CMD]  
    • Lưu ý: Nếu là công việc cron hệ thống Linux nằm trong /etc/cron.d, sẽ có một trường thứ sáu chỉ định người DÙNG nào sẽ chạy cron đó (xem ví dụ /etc/cron.d/raid-check) 
    • Lưu ý: Trong trường Ngày trong tuần, số 0 và 7 đều chỉ là Chủ nhật 
    • Lưu ý: Với giờ, 0 là nửa đêm  

• Mỗi cột phải có một giá trị, ngay cả khi giá trị là * có nghĩa là áp dụng cho tất cả các giá trị có thể trong trường 
	• Ví dụ: 30 23 * 2 7  
    • Công việc này sẽ được lên lịch vào 30 phút sau 23 giờ trong ngày (11:30 PM), vào bất kỳ ngày nào của tháng 2 cũng là ngày Chủ nhật  
    • Lưu ý: Bằng cách sử dụng viết tắt ba chữ cái, bạn có thể thay thế tên của tháng cho trường thứ tư cũng như tên của ngày cho trường thứ năm  
    • Ví dụ: 30 23 * feb sun 
    • Tương đương với ví dụ trước đó  

 • Khoảng giá trị 
    • Một khoảng giá trị có thể được xử lý bằng cách sử dụng dấu gạch ngang giữa hai giá trị 
    • Ví dụ: 30 23 * 2-4 7  
        • Công việc này sẽ được lên lịch vào 30 phút sau 23 giờ trong ngày (11:30 PM), vào bất kỳ ngày nào của các tháng từ tháng 2 đến tháng 4, cũng là ngày Chủ nhật

• Cũng có thể được chỉ định bằng danh sách phân cách bằng dấu phẩy  
    • Ví dụ: 30 23 * 2,3,12 1,3  
        • Công việc này sẽ được lên lịch vào 30 phút sau 23 giờ trong ngày (11:30 PM), vào bất kỳ ngày nào của các tháng tháng 2, tháng 3 và tháng 12, cũng là thứ Hai hoặc thứ Tư  

• Giá trị cũng có thể được chỉ định dưới dạng "bước" 
  • Ví dụ: 0 * /4 * 2,3,12 1,3 
    	• Công việc này sẽ được lên lịch vào đầu giờ, bốn giờ một lần, vào bất kỳ ngày nào của các tháng tháng 2, tháng 3 và tháng 12, cũng là thứ Hai hoặc thứ Tư  

• Công việc / lệnh để chạy

  • Mọi lệnh shell hợp lệ, ứng dụng hoặc kịch bản
    	• Lưu ý: Công việc cron cho một người dùng sẽ có môi trường rất giới hạn (.bash_profile, .bashrc, .bash_login, vv.) không chạy, vì vậy cần cung cấp đầy đủ đường dẫn đến các lệnh và biến trong kịch bản, nếu không bạn có thể gặp lỗi hoặc kết quả không mong muốn (ví dụ: PATH chỉ có /usr/bin và /bin)
        • Lưu ý: Bạn có thể đặt một số biến môi trường đặc biệt trước công việc của bạn
      	• MAILTO: Đầu ra từ công việc sẽ được gửi qua email đến địa chỉ được chỉ định  
        • SHELL: Chạy công việc với shell được chỉ định  
        • CRON_TZ: Sử dụng múi giờ được chỉ định cho crontab

• Chuyển hướng công việc
 
   • Ngoại trừ biến MAILTO đã được đề cập, bạn có thể chuyển hướng đầu ra vào /dev/null hoặc một file khác
        • Ví dụ: 0 * /4 * 2,3,12 1,3 /path/application/script.sh > /dev/null  
            • Sẽ "loại bỏ" toàn bộ đầu ra (/dev/null)
        • Ví dụ: 0 * /4 * 2,3,12 1,3 /path/application/script.sh 2>&1 > /root/some.log  
            • Sẽ lấy toàn bộ đầu ra chuẩn và lỗi và chuyển hướng vào file/root/some.log

## /var/spool/cron

• Tất cả các crontab của người dùng được tạo / chỉnh sửa bằng crontab được lưu tại đây    

## /etc/cron.allow

• Whitelist (Danh sách trắng) của các người dùng được phép chạy các công việc cron

• Nếu file này tồn tại và trống, thì chỉ root mới có thể truy cập vào crontabs 

## /etc/cron.deny

• Blacklist(Danh sách đen) chứa tên người dùng users không được phép chạy các công việc cron

• Nếu file này tồn tại và trống, tất cả các người dùng có thể truy cập vào crontabs và chạy công việc

• Lưu ý: Thứ tự ưu tiên sẽ áp dụng cron.allow và bỏ qua cron.deny nếu nó tồn tại     