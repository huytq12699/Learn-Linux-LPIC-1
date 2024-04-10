# Tìm kiếm file văn bản

### Lệnh `grep`  

- Một tiện ích để tìm chuỗi và cụm từ trong tập tin, luồng hoặc thư mục.  

- Đại diện cho - in ra các biểu thức chính quy toàn cầu 

- `-c`: chỉ hiển thị số lượng tìm thấy.

- `-C [#]`: bao quanh kết quả tìm kiếm với '#' dòng thông tin liên quan (trước và sau dữ liệu)  

- `-E [ext. regex]`: sử dụng biểu thức chính quy mở rộng chỉ định để tìm kiếm.  

- `-F [fixed regex]`: sử dụng biểu thức chính quy cố định chỉ định để tìm kiếm. 

- `-H`: hiển thị tên file của mỗi chuỗi hoặc cụm từ khớp.  

- `-h`: ngăn không hiển thị tên file. 

- `-i`: không phân biệt chữ hoa chữ thường.  

- `-l`: chỉ hiển thị tên file, không hiển thị chuỗi/cụm từ khớp.  

- `-L`: chỉ hiển thị tên file không chứa chuỗi/cụm từ khớp.  

- `-w`: chỉ khớp các dòng chứa toàn bộ chuỗi hoặc cụm từ.

- `-x`: chỉ hiển thị các dòng khớp chính xác toàn bộ chuỗi hoặc cụm từ. 

- `-v`: chỉ hiển thị các dòng trong file không khớp với chuỗi hoặc cụm từ (ngược lại với mặc định)

- Ví dụ

	```sh 
	find / -name "*.sh" -exec grep -iH "modprobe" {} ;  
	```
	+ Lệnh này sẽ tìm file, đệ quy, bắt đầu từ thư mục `root` và kết thúc bằng `.sh`, truyền file đó cho lệnh `grep`, lệnh này sẽ không phân biệt chữ hoa chữ thường và hiển thị tên file và nội dung khớp của bất kỳ file nào chứa từ 'modprobe'

- Ví dụ 

	```sh
	grep -cv "/bin/bash" /etc/passwd
	```  
	+ Sẽ chỉ hiển thị các dòng không chứa giá trị `/bin/bash` và hiển thị số lượng (ví dụ: bạn sẽ biết số lượng tài khoản người dùng không có bash được liệt kê là shell mặc định)

### Lệnh `egrep`

- Lệnh grep mà không cần chỉ định -E  

- Cho phép sử dụng biểu thức chính quy mở rộng để khớp các mẫu văn bản  

- Ví dụ:

	```sh

	'egrep '^ope(n|r)' /etc/passwd'
	```  
	+ Lệnh này sẽ hiển thị các mục nhập trong file `/etc/passwd` mà bắt đầu bằng `ope` và tiếp theo là `n` hoặc `r` (sau đó là bất kỳ ký tự nào khác), 
	ví dụ như `openvpn` hoặc `operator`.

- Ta cũng có thể sử dụng toán tử `OR (|) `để tạo mẫu tìm kiếm phức tạp hơn.  

	+ Ví dụ: 

	```sh
	egrep '(bin|bash)' /etc/passwd
	```  
	+ Lệnh trên sẽ hiển thị các dòng chứa từ `bin` hoặc `bash` trong `file /etc/passwd`.    

### Lệnh `fgrep`  

- Là lệnh Grep mà không cần chỉ định -F  

- Cho phép sử dụng một file chứa một hoặc nhiều mục để tìm kiếm (tìm kiếm file) 

- `-f [itemfile]`: sử dụng file chỉ định là danh sách các mục để tìm kiếm trong file được chỉ định  

- Ví dụ:

	```sh 
	fgrep -f itemfile.txt searchfile.txt
	```
	+ Lệnh trên sẽ sử dụng các mục trong `itemfile.txt` làm tham số tìm kiếm cho tất cả các dòng trong `searchfile.txt` và hiển thị các kết quả tìm kiếm.

### Biểu thức chính quy

- Là phương pháp tìm kiếm chuỗi hoặc cụm từ không biết chính xác bằng cách sử dụng chuỗi bán phần và ký tự đặc biệt.  

- Các ký tự biểu thức chính quy:

	+ `.`: phù hợp với bất kỳ ký tự đơn nào  

	+ `*`: phù hợp với từ '0 đến n' ký tự trong một chuỗi 

	+ `?`: phù hợp với một mục tùy chọn, nhưng chỉ một lần

	+ `+`: mục PHẢI được phù hợp ít nhất một lần nhưng có thể được phù hợp nhiều hơn

	+ `{#}`: phù hợp '#' lần  
	
	+ `{#,}`: phù hợp '#' lần hoặc nhiều hơn  
	
	+ `{#,#}`: phù hợp giữa số đầu tiên và số thứ hai (ví dụ: {3,10} có nghĩa là phù hợp từ 3 đến 10 lần)  

	+ `<`: từ bắt đầu bằng chuỗi sau  

	+ `^`: từ bắt đầu bằng chuỗi sau  

	+ `>`: từ kết thúc bằng chuỗi sau  

	+ `$`: từ kết thúc bằng chuỗi sau  

	+ `[abc]`: tìm kiếm bất kỳ ký tự trong danh sách

	+ `[^abc]`: tìm kiếm bất kỳ ký tự nào ngoại trừ các ký tự trong danh sách, không phân biệt chữ hoa hay chữ thường

	+ `[0-9]`: tìm kiếm bất kỳ ký tự nào trong một phạm vi là các con số từ 0 đến 9.

	+ `[^o]`: các từ không chứa chữ cái 'o' 
		
		+ Ví dụ 

		```sh
		grep “d[^o]g” textfile.txt
		```  
		+ Lệnh trên sẽ trả về các từ bắt đầu bằng 'd' và kết thúc bằng 'g' và có bất kỳ chữ cái nào ngoại trừ 'o' ở giữa (ví dụ: dig, dug) 

	+ `^...$`: bất kỳ dòng nào chứa chính xác ba ký tự  
 		
 		+ Ví dụ 1

 		```sh
 		grep “<ope[^r]” /etc/passwd
 		```  
		+ lệnh trên sẽ hiển thị các từ bắt đầu bằng 'ope' theo sau bởi bất kỳ chữ cái nào TRỪ 'r' trong file /etc/passwd 
		(ví dụ: tìm tài khoản 'openvpn' nhưng không tìm 'operator') 
		
		+ Ví dụ 2

		```sh
		grep “nologin>” /etc/passwd
		```  
		+ lệnh trên sẽ hiển thị tất cả các từ kết thúc bằng 'nologin' trong tệp /etc/passwd