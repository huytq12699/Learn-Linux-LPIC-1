# Shell, Biến, Thiết lập và Source

1. Shell đặc biệt

- `/bin/false` Trả về một mã khác không để chặn bất cứ yêu cầu đăng nhập(login) của người dùng nào.

- `/sbin/nologin` Cũng chặn yêu cầu đăng nhập, nhưng trả về một thông báo kết quả  dưới dạng văn bản.

2. Biến (môi trường)

- "Lối tắt(shortcut)" đến nhiều giá trị và loại khác nhau.

	+ Ví dụ: `NUMBER=123456`


     > Việc này sẽ tạo một biến môi trường được gọi là `NUMBER` và gán giá trị số ban đầu là `123456` vào biến đó

- Có thể hiển thị trên dòng lệnh (hoặc sử dụng như một phần của một lệnh hoặc thay thế) bằng cách đặt ký tự `$` trước biến.

	+ Ví dụ: `echo $NUMBER`


	 > Sẽ hiển thị giá trị hiện tại của biến `NUMBER` (trong ví dụ trước đó, giá trị này sẽ là 123456)

- Biến có thể là số hoặc văn bản và biến văn bản có thể chứa khoảng trắng nếu được đặt trong dấu ngoặc kép hoặc trích dẫn.

 	+ Ví dụ: `MYVAR= ="Space Value"` hoặc `MYVAR=Space\ Value`

- Export

	+ Hiển thị các biến đã xuất (khi chạy riêng lẻ)

	+ Từ khóa, khi đặt trước một biến, cho phép giá trị của biến được truyền cho các shell khác hoặc các tiến trình con của shell hiện tại 
(hành vi bình thường là giá trị biến chỉ được hiển thị trong shell hiện tại, gọi là phạm vi biến)

	+ Ví dụ:  

      + `NUMBER=123 * echo $[NUMBER*2]`

         > Kết quả sẽ trả về giá trị 246

      + Khi thoát khỏi phiên bash hiện tại và tạo một phiên bash mới, giá trị của biến sẽ không được 
      chuyển sang phiên con mới

3. Source (sử dụng các giá trị từ một file khác)

 - Tương đương với việc bao gồm các giá trị được chỉ định trong một file vào một lệnh khác, shell hoặc lệnh khác.

 	+ Ví dụ: file `sourcefile.sh` chứa biến `NUMBER=123`

      • Lấy giá trị biến từ `sourcefile.sh` vào shell hiện tại: `source ./sourcefile.sh`

      • `echo $NUMBER` từ dấu nhắc lệnh bash sau đó sẽ hiển thị giá trị `123` trong biến

 - Phím tắt cho việc sourcing

    + Ví dụ: `source ./sourcefile.sh` có thể được thay thế bằng `../sourcefile.sh ` 

4. `unset`

- Các biến có thể được gỡ bỏ bằng lệnh unset

   + Ví dụ: `unset NUMBER && echo $NUMBER`

   	> Trong ví dụ của chúng ta, kết quả sẽ tạo ra đầu ra có giá trị trống vì nó gỡ bỏ biến

5. `set`

- Hiển thị tất cả các biến và hàm trong môi trường hiện tại

- Cũng cho phép kích hoạt/tắt các tính năng shell khác nhau 

   • Ví dụ: `set –x` 

- Sẽ in từng lệnh ra terminal khi được thực thi

   • Ví dụ: `set +x` 

- Sẽ tắt (disable) việc in từng lệnh ra terminal  


# Môi trường và Bí danh

1. `env` 

+ Khi chạy lệnh này độc lập(không có tham số gì), hiển thị các biến môi trường hiện tại và giá trị của chúng.

+ Có thể được sử dụng để sửa đổi môi trường hiện tại trước khi bạn chạy một lệnh (hoặc một tập lệnh khi được 
sử dụng ở trên cùng của các dòng lệnh)

+ Thường được sử dụng để xóa môi trường hiện tại trước khi thực hiện một thao tác gì đó.

2. `alias`

- Cho phép bạn thay thế một lệnh bằng lệnh khác hoặc đặt một lối tắt bằng một lệnh phức tạp hơn với các chuyển đổi

- Có thể được sử dụng để ghi đè lên một lệnh hiện có 

3. `unalias` Xóa (trong môi trường hiện tại) bí danh được chỉ định 

4. `/etc/profile` Đây là file được đọc đầu tiên trong một phiên đăng nhập. Nó thiết lập các biến môi trường 
trên toàn hệ điều hành, giá trị umask, kiểm soát lịch sử Bash(history), ...

5. `/etc/profile.d` Đây là thư mục chứa các file script cấu hình bổ sung cho Bash

6. `/etc/bashrc` Trong file này, bạn có thể cấu hình các chức năng và alias trên toàn hệ thống

7. `/etc/skel` Đây là thư mục chứa các file mặc đinh như `.bash_profile`, `.bashrc` và 
các file khác được thêm vào thư mục `home` của người dùng khi tài khoản được tạo trên HĐH

8. `~/.bash_profile` File này có thể chứa biến môi trường PATH được sửa đổi của người dùng và 
sẽ kế thừa nội dung từ file `~/.bash.rc`

9. `~/.bash_logout` File này được gọi khi người dùng đăng xuất và có thể được sử dụng để tắt ứng dụng, 
hiển thị thông điệp hoặc thực hiện các tác vụ dọn dẹp môi trường khác

10. `~/.bash_login` File này được gọi khi người dùng đăng nhập. 
Thông thường, các file `.bash_profile` và `.bashrc` được sử dụng thay vì file này
