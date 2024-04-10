# Các Biến môi trường - Hiển thị, Thiết lập và Sử dụng

### Biến môi trường  

- 'Phím tắt' cho phép bạn chỉ định đường dẫn, lệnh, bí danh (aliases)hoặc thông tin khác với một ký hiệu dễ sử dụng và dễ nhớ.

### env

- Lệnh để liệt kê tất cả các biến môi trường được thiết lập cho phiên làm việc hiện tại 
TRỪ các thiết lập của shell  

### set  

- Dùng để xem các thiết lập của shell hoặc biến shell nào cho phiên làm việc. 

- Có thể dùng để bật hoặc tắt các tùy chọn shell

    + `-o [option]` – ON (bật) tùy chọn  
    
    + `+o [option]` – OFF (tắt) tùy chọn  

- Các tùy chọn có sẵn

	- `vi` hoặc `emacs` - kiểu bàn phím cho dòng lệnh

	- `hashall` - mặc định BẬT, cho phép bảng băm lệnh và vị trí được sử dụng lặp lại  

	- `history` - mặc định BẬT, cho phép đọc HISTFILE để tìm file lịch sử (xem bên dưới)  

	- `monitor` - chạy các tiến trình nền trong một nhóm khác và thông báo cho console khi chúng hoàn thành  

	- `noclobber` - mặc định TẮT, không cho phép chuyển hướng '>' ghi đè lên một file đã tồn tại

	- `noexec` - mặc định TẮT, các files kịch bản(script) sẽ chạy kiểm tra cú pháp khi bật trên tất cả các lệnh khi chạy

	- `notify` - công việc kết thúc thông báo ngay lập tức trên console thay vì trong lần thực thi tiếp theo của lệnh 'jobs'  

	- `verbose` - hiển thị lệnh ra terminal/màn hình trước khi chúng được thực thi

### shopt  

- Dùng để xem bất kỳ thiết lập của shell hoặc biến shell nào cho phiên làm việc  

### PATH  

- Một biến môi trường chứa danh sách các thư mục được phân tách bằng dấu hai  chấm (:) được tìm kiếm (theo thứ tự) để tìm các file thực thi lệnh (nghĩa là các file có quyền thực thi) 

- Đường dẫn tuyệt đối - `/home/user/command`

- Đường dẫn tương đối - `./command`

- Thông thường biến môi trường PATH được thiết lập ban đầu (cho hệ thống Linux) trong file /etc/profile

- PATH có thể được thay đổi trên dòng lệnh hoặc các files cấu hình khác chứa các tập lệnh thực thi (ví dụ: /home/user/.bashrc)

	+ Ví dụ (trong file /etc/profile) - export PATH=/sbin:/bin:/usr/bin:/usr/local/bin

- Thiết lập các vị trí thư mục 'bin' chung cho các files thực thi trên hệ thống Linux

	+ Ví dụ về PATH được thay đổi trong file /home/user/.bashrc - export PATH=$PATH:/home/user/bin

- Lấy giá trị hiện tại (không bao gồm $PATH sẽ ghi đè lên giá trị hiện tại, làm mất nó) và thêm vào cuối /home/user/bin để người dùng có thể đặt các files tập lệnh riêng trong thư mục đó và thực thi mà không cần cung cấp đường dẫn tuyệt đối đến chúng

### HISTFILE

• Lệnh history sử dụng giá trị này để hiển thị danh sách các lệnh đã chạy trước đó

• Theo mặc định, giá trị của nó cho bất kỳ người dùng nào sẽ là /home/user/.bash_history

• `HISTCMD` - chỉ mục của lệnh hiện tại.

• `HISTCONTROL` - khi được thiết lập thành ignorespace, bất kỳ lệnh nào đi trước bởi một khoảng trắng sẽ KHÔNG được ghi lại trong file lịch sử, khi được thiết lập thành ignoredups, hai dòng liên tiếp giống nhau sẽ có một dòng bị bỏ qua

• `HISTFILESIZE` - số dòng có thể chứa các lệnh trước đó (mặc định là 500)

### Thay đổi biến môi trường

- Tất cả các biến có thể được thay đổi theo 2 cách:

	+ Ghi đè (export VARIABLE=newValue)

	+ Thêm vào (export VARIABLE=$VARIABLE:newValue)

- Sử dụng biến môi trường trên dòng lệnh.  

	+ `echo [$ + tên biến]` - sẽ hiển thị giá trị hiện tại

        + Ví dụ - `echo $HOME`

            + Sẽ hiển thị thư mục gốc của người dùng hiện tại đã được thiết lập trong biến đó  
        
        + Ví dụ - `cd $HOME` (hoặc cd ~/)  
            
            + Sẽ đổi thư mục hiện tại của shell thành thư mục gốc của người dùng hiện tại (xem danh sách các ký tự đặc biệt trong shell ở phần trên)                                                      