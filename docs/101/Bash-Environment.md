# Linux Shell

Shell là môi trường dòng lệnh mà bạn làm việc trong hệ thống Linux
- `bash(bourne again shell)`: mặc định

- `csh`: cú phép lập trình C

- `ksh - KornShell`: dựa trên Bourne Shell với một số tính năng của C Shell được thêm vào

- `zsh - Z Shell`: bao gồm các yếu tố của Bash Shell và Korn Shell

# Bash Environment

## Môi trường Bash
- Biến môi trường: 
	+ các thiết lập quy định chức năng chung và vị trí cho các mục đích khác nhau
	+ cú pháp: 
	   ```sh
	   VARIABLE=path,command,alias
	     (BIẾN=đường dẫn,lệnh,bí danh)
	     ```
	Ví dụ: 
		```sh
		CWD=/home/user/Documents
		```

## Bash Funcition(Hàm)
- Người dùng có thể tạo các hàm tùy chỉnh của riêng mình trong Bash
- Ví dụ:
	```sh
		 function hello()
			{
			echo "Hello World!"
		 	}
		 ```

## Các câu lệnh trong Bash Environment

+ `env` Lệnh hiển thị các biến môi trường

+ `echo` Lệnh đa dụng có thể được sử dụng để in giá trị của một biến lên màn hình

+ `set` Hiển thị các thiết lập shell hoặc các biến shell cho phiên làm việc trong môi trường shell

+ `unset` Xóa một biến hoặc chức năng bash tùy chỉnh

+ `shopt` Hiển thị các tùy chọn shell và cài đặt hiện tại của chúng

+ `export` Được sử dụng để xuất 1 biến đến shell hiện tại và bất kỳ shell mới nào được bắt đầu từ shell hiện tại

+ `pwd` Hiển thị đường dẫn đầy đủ tới thư mục làm việc hiện tại

+ `which` Được sử dụng để tìm vị trí của một file ứng dụng nằm trong PATH của người dùng

+ `type` Được sử dụng để xác định kiểu của một đối tượng như là một hàm, file bí danh, tích hợp sẵn hoặc từ khóa
```sh 
		VD: "type type" sẽ hiển thị loại của lênh "type"
		```

+ Trích dẫn 'yếu' hay còn gọi dấu ngoặc kép: Mở rộng các biến nhưng các ký tự được sử dụng cho việc thay thế đường dẫn 
hoặc cho phép so khớp sẽ không được mở rộng
```sh
		VD: `echo "$PATH"`, hiển thị lên giá trị của biến `PATH`
 			`ls"*"` sẽ không hoạt động vì lệnh `ls` sẽ tìm kiếm tập tin có tên là '*'
 		```

+ Trích dẫn 'mạnh': Bên trong trích dẫn mạnh hoặc dấu ngoặc đơn, không có gì được thực thi
```sh
	VD: `echo "$PATH"` sẽ in ra `$PATH` trên màn hình
	```

+`history` Là một lệnh tích hợp sẵn trong Bash shell, được sử dụng để hiển thị danh sách các lệnh 
đã được thực thi trước đó