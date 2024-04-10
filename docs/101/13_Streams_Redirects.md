# Sử dụng Luồng(Streams) và Chuyển hướng (Redirects)

## Streams

1. Luồng đầu vào tiêu chuẩn (Standard input stream) 

- Một luồng cung cấp đầu vào cho các thiết bị đầu cuối, files, các ứng dụng và/hoặc tiện ích (phương thức mà tất cả các chương trình được cho là có thể chấp nhận trong một số hình thức) 

2. Luồng đầu ra tiêu chuẩn (Standard output stream) 

- Luồng đầu ra tiêu chuẩn 

	+ Một luồng cung cấp đầu ra cho các thiết bị đầu cuối, file, ứng dụng và/hoặc tiện ích  

- Luồng lỗi tiêu chuẩn(Standard error stream)  
 
	+ Một luồng chứa các thông báo lỗi được đưa ra đến các thiết bị đầu cuối, file, ứng dụng và/hoặc tiện ích (được coi là tập hợp con của luồng đầu ra tiêu chuẩn)

## Redirects

1. Chuyển hướng(Redirection)  

- Quá trình lấy một luồng và gửi nó "đến nơi khác", không phải là mặc định  

- Các thiết bị 

	+ Đầu vào tiêu chuẩn(Standard input) - /dev/stdin  
	
	+ Đầu ra tiêu chuẩn(Standard output) - /dev/stdout  

	+ Luồng lỗi tiêu chuẩn(Standard error) - /dev/stderr  

- Bộ chỉ số tập tin và tập tin liên quan

	+ Đầu vào tiêu chuẩn - chỉ số file 0 - file /proc/self/fd/0  
	
	+ Đầu ra tiêu chuẩn - chỉ số file 1 - file /proc/self/fd/1  

	+ Luồng lỗi tiêu chuẩn - chỉ số file 2 - file /proc/self/fd/2 

2. Trình chuyển hướng(Redirectors)  

- `|`: đường ống, để gửi đầu ra lệnh đến lệnh khác  

	+ Ví dụ 

	```sh
	cat /var/log/messages | more  
	```

- `>`: chuyển hướng đầu ra tiêu chuẩn đến một file hoặc thiết bị (tạo hoặc ghi đè đích nếu là một file)  

	+ Ví dụ:

	```sh
	find /user -name *.sh > output.txt
	```

- `>>`: chuyển hướng đầu ra tiêu chuẩn đến một file hoặc thiết bị (nối thêm vào đích nếu là một file)  

	+ Ví dụ

	```sh
	find /user -name "*.txt" >> output.txt  
	```

- `<`: chuyển hướng đầu vào tiêu chuẩn đến một chương trình  

	+ Ví dụ

	```sh
	sort < /home/user/listfile.txt 
	```

3. Chuyển hướng luồng lỗi (Redirecting standard error)  

- Thông thường, stderr được chuyển hướng đến một file (ghi nhật ký log) hoặc một thiết bị đặc biệt gọi là /dev/null 

- Việc này cho phép bạn xóa các lỗi từ đầu ra tiêu chuẩn bình thường 

	+ Ví dụ 
	
	```sh
	find / -iname "*.sh" 2> /dev/null
	``` 
	+ Sẽ hiển thị kết quả của các kết quả tìm thấy mà không hiển thị các thông báo lỗi liên quan đến quyền truy cập 

4. Kết hợp chuyển hướng 

- Ví dụ 

	```sh
	find / -iname "*.sh" 2> /dev/null > output.txt
	```
	+ Tương tự như ví dụ trên, nhưng các kết quả sẽ được chuyển hướng đến file `output.txt` thay vì hiển thị lên trên màn hình

- Ví dụ 

	```sh
	sort < listfile | nl
	```
	+ Chuyển hướng 'listfile' như một luồng đầu vào đến lệnh `sort`, đẩy đầu ra đó vào lệnh `nl` để thêm số dòng, hiển thị lên màn hình 

5. Kết hợp đặc biệt 

- Thường được sử dụng để loại bỏ toàn bộ đầu ra cho một công việc(job) hoặc tiến trình process (như một công việc cron), để đảm bảo không gây ra các lỗi trong hiển thị dữ liệu. 

- Ví dụ 
	
	```sh
	find / -iname ".sh" > /dev/null 2>&1
	``` 
	+ Chuyển hướng lỗi tiêu chuẩn thành đầu ra tiêu chuẩn (2>&1) và toàn bộ luồng đầu ra được chuyển hướng vào `/dev/null` (bị loại bỏ) 

6. `tee` 

- Đọc dữ liệu từ stdin, viết dữ liệu đó ra stdout và các files. Lệnh này hữu ích để kết nối các lệnh dài với nhau và xem đầu ra ở các giai đoạn khác nhau.

- Thường được sử dụng khi bạn muốn thu thập đầu ra của một ứng dụng nhưng cũng cần nhìn thấy kết quả trên màn hình. 

- Ví dụ

	```sh
 	find / -name "*.sh" | tee visibleresults.txt
 	``` 
	+ Sẽ tìm tất cả các file có đuôi mở rộng `*.sh` từ phân vùng gốc(root partition), đẩy kết quả đó như một luồng đầu vào cho `tee`, sau đó mở hai luồng đầu ra tiêu chuẩn, gửi một luồng đến console và một luồng đến file được chỉ định `visibleresults.txt`

7. `xargs` 

- Nhận đầu vào từ stdin và các lệnh khác. Thông thường được sử dụng với lệnh `find` nhưng cũng có thể sử dụng với các lệnh khác sau đó đẩy chúng vào một lệnh khác theo yêu cầu. 

- Ví dụ

	```sh
	find / -name "*.sh" | xargs ls -al > myresults.txt  
    ```                     
    + Sẽ tìm tất cả các files có đuôi mở rộng `*.sh`, sau đó `xargs` sẽ lấy kết quả đó và cung cấp cho lệnh `ls -al` để hiển thị chi tiết của mỗi file và chuyển hướng đầu ra vào file `myresults.txt`