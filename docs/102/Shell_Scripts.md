# Shell_Scripts

1. Mục đích

- Giảm công việc phải lặp đi lặp lại.

- Rất hữu ích nếu chúng ta sử dụng kịch bản Scripts để tự động hóa cho công việc.

2. Shell_scripts căn bản

- `#!` Chuỗi ký tự (được biết đến với tên gọi"shebang") có thể được sử dụng ở đầu của bất kỳ tập lệnh Perl, Python hoặc Bash nào. Chuỗi này cho HĐH biết là file đó là một tập lệnh.

- `#(comment)` Giải thích ý nghĩa của mã lệnh là gì.

- `Commands` Là các dòng mã lệnh tạo nên tệp tập lệnh. 

- `Quyền thực thi` Tệp tập lệnh phải có quyền thực thi được thiết lập trên nó để sử dụng.

- `Parameters` Các tham số là các mục được chuyển đến tập lệnh. Tập lệnh shell thực hiện các tham số này (hoặc đối số) theo vị trí, có nghĩa là vị trí của tham số xác định giá trị của biến được gán cho nó.

	+ VD: command option1 option2

3. Cách thêm điều kiện và xử lý logic với Bash Shell Scipts

- Lệnh `if,else,elseif và fi` được sử dụng để kiểm tra tính hợp lệ của một biểu thức trong Linux.

- Lệnh `test` được sử dụng để kiểm tra các điều kiện khác nhau.

- `| |` Hai dấu pipe đặt cạnh nhau biêt thị cho một phép toán OR logic. Khi một trong hai điều kiện được kiểm tra là đúng thì biểu thức đó được xác định là đúng.

- `&&` Phép toán AND logic được sử dụng để kiểm tra tính đúng đắn của hai điều kiện. Nếu cả 2 điều kiện đều đúng thì biểu thức đó được xác định là đúng.

- `=` Dấu bằng được sử dụng để kiểm tra sự bằng nhau của một câu lệnh.

- `!=` Dấu này biểu thị sự không bằng nhau của 2 câu lệnh
