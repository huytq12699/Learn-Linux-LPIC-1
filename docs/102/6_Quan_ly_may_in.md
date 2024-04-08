# Quản lý máy in và in ấn (CUPS và lpr)

### lpd

- Lệnh dịch vụ in truyền thống trước khi có CUPS, là phương pháp mặc định để gửi đầu ra đến máy in/thiết bị in ấn  

- Lưu ý: Vì mục đích thực hành, bạn sẽ cài đặt lpd, cài đặt gói cups-lpd để chúng hoạt động với các lệnh cũ và cài đặt cups-pdf để cài đặt máy in để làm việc 

### ipp  

- Giao thức in internet (dựa trên web) 

### CUPS  
 
- Hệ thống in chung của HĐH Unix  

- Kết hợp của các công cụ chuyển đổi, bộ lọc và "trình điều khiển(driver) máy in" mà tài liệu có thể được gửi đến khi đầu ra đến các thiết bị in ấn, các kịch bản để tạo tài liệu định dạng SVG, PDF hoặc định dạng khác 

### cupsd

- Tiến trình nền (daemon) cho CUPS  

- CUPS hoạt động trên cổng 631 và có thể truy cập thông qua trình duyệt local của bạn (http://localhost:631) 

### /etc/cups  

- Thư mục cấu hình cho CUPS  

- Danh sách các files cấu hình:  
    
    + `classes.conf`: Cấu hình định nghĩa các lớp  
    
    + `cupsd.conf`: file cấu hình chính cho tiến trình nền (daemon)  
    
    + `cupsd.conf.default`: file cấu hình mặc định mẫu để khôi phục dự phòng  
    
    + `printers.conf`: Cấu hình của từng máy in trên hệ thống  
    
    + `ppd`: Thư mục PPD (file trình điều khiển máy in) trên mỗi máy in trên hệ thống 

### cupsreject  

- Được sử dụng để đặt máy in từ chối tất cả các công việc in đã được gửi đến nó. Bằng  cách chỉ định tên máy in, lệnh này sẽ chặn tất cả các công việc in tiếp theo được gửi đến máy in đó. 

### cupsaccept  

- Bằng cách chỉ định tên máy in, lệnh này sẽ đặt máy in đó chấp nhận tất cả các công việc in đã được gửi đến nó. 

### cupdisable  
 
- Vô hiệu hóa máy in đã chỉ định (nhưng vẫn chấp nhận công việc in, chỉ giữ trong hàng đợi). 

### cupsenable

- Kích hoạt máy in đã chỉ định. 

### cupsctl  
 
- Sử dụng để điều khiển cấu hình CUPS, chạy mà không có tùy chọn, hiển thị cấu hình hiện tại. 

### lpadmin  

- Tiện ích tương thích với lp để quản lý hàng đợi lp (nhớ là plugin tương thích với CUPS, do đó sẽ áp dụng cho toàn bộ cấu hình in cục bộ).  

- Có thể cấu hình để thêm một máy in test bằng lệnh sau:  
    
    + `lpadmin -p MyTestPrinter -E -v /dev/null -m raw` 

### lpstat  

-  Hiển thị cấu hình lp hiện tại (máy in và mặc định). 
 	
	+ `-p`: Hiển thị máy in

 	+ `-d`: Hiển thị mặc định

 	+ `-a`: Hiển thị tất cả hàng đợi in và trạng thái 

 	+ `-r`: Trạng thái dịch vụ

 	+ `-s`: Tổng quan cấu hình hệ thống 

 	+ `-t`: Tổng quan chi tiết cấu hình hệ thống 

### lpoptions

- Cho phép đặt các tùy chọn máy in từ dòng lệnh.  

	+ `-d [máy in]`: Đặt máy in mặc định thành giá trị đã chỉ định.  
	
	+ `-p [máy in]`: Xử lý máy in đã chỉ định.  
	
	+ `-l`: Liệt kê các tùy chọn cho máy in/hàng đợi đã chỉ định. 
    	
    	+ Ví dụ: `lpoptions -p CUPS-PDF -l`  
       		
       		+ Sẽ hiển thị tất cả các tùy chọn cho máy in CUPS-PDF.

### lp  
  
- Các công cụ dòng lệnh (cổ điển) để in.

    + Ví dụ: `echo "my test print job" | lp` 

### lpr 

- Là các công cụ dòng lệnh (cổ điển) để in tài liệu.

   	+ Ví dụ: `echo "công việc in kiểm tra của tôi" | lpr` 
        
        + Sẽ in kết quả của lệnh echo vào máy in mặc định. 
        
        + `-P [printer]`: Máy in đích (nếu không phải máy in mặc định). 
       	
       	+ `-#[#]`: In số bản sao được chỉ định. 

### lpq 

- Hiển thị hàng đợi in và công việc in.

- `-a`: Hiển thị tất cả công việc in cho tất cả máy in.

- `-P [printer]`: Hiển thị công việc in cho máy in được chỉ định. 

### lprm

- Cho phép bạn xóa công việc in.

- Lưu ý: Chạy lệnh mà không có một job ID sẽ xóa công việc in đầu tiên trong hàng đợi. 

- `-P [printer]`: Làm việc với máy in được chỉ định. 

- `-a`: Xóa tất cả các công việc in trong hàng đợi.