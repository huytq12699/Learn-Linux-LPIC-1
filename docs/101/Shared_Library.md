# THƯ VIỆN CHIA SẺ(Shared library)

- Các file chứa chức năng mà các chương trình ứng dụng khác có thể sử dụng

- Các files này thường được lưu trữ trong các files định dạng `.so`

- Có thể tìm thấy các file này tỏng thư mục sau:

 	+ `/lib`

	+ `/usr/lib (32 bit)` và `/usr/lib64 (64 bit)`

	+ `/usr/local/lib`

	+ `/usr/share`

- Có 2 kiểu files thư viện:

	+ File Thư viện động Dynamic( kết thúc trong `.so`)

	+ File Thư viện liên kết tĩnh Statically linked( kết thúc trong `.a`)

## CÁC CÂU LỆNH QUẢN LÝ THƯ VIỆN CHIA SẺ

- `ldd`: Liệt kê ra các đối tượng phụ thuộc được chia sẻ

- `ldconfig`: Cấu hình các liên kết thời gian chạy trình liên kết động, tạo bộ đệm dựa trên thư mục thư viện 
và có thể hiển thị cho bạn những gì hiện được lưu trong bộ đệm(cache)

- `/etc/ld.so.conf`: Là file cấu hình trỏ đến các thư mục và các file cấu hình khác chứa tham chiếu đến 
các vị trí thư mục thư viện

- `LD_LIBRARY_PATH`: Là biến môi trường kế thừa trỏ đến một đường dẫn mà các file thư viện có thể 
được đọc từ đường dẫn này