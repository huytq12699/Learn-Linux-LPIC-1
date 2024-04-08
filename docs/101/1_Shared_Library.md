# Thư Viện Chia Sẻ (Shared Library)

- Các hàm có thể được sử dụng lại bởi các ứng dụng khác thông qua việc 'liên kết' với chúng trong file thư viện  
    
    + Bất kỳ tên file thư viện chia sẻ nào đều có đuôi mở rộng '.so' (có thể cũng chứa thông tin phiên bản sau phần mở rộng .so)  
    
    + 'so' trong tên đuôi mở rộng đại diện cho 'shared object' (đối tượng chia sẻ)  
    
    + /lib  
    
    + /usr/lib/* (/usr/lib64/* - cho thư viện 64 bit)  
    
    + /usr/local/lib/*  
    
    + /usr/share/*  
    
    + Vị trí phổ biến cho các thư viện chia sẻ của hệ thống Linux

### Liên kết   

1. Liên kết mềm  

• Rất nhiều lần, các phiên bản cụ thể của thư viện được liên kết với một tên chung.  

• Ví dụ:

```sh
libstdc++.so > libstdc++.so.6.0.19
```

2. Liên kết tĩnh 

- ứng dụng chứa một bản sao đầy đủ của thư viện được sử dụng.  
    
- Ưu điểm:

    + kiểm soát phiên bản (ứng dụng sẽ có phiên bản thư viện chính xác mà nó có thể cung cấp với các giao diện đã biết)  

- Nhược điểm:

	+ kích thước (tăng kích cỡ của ứng dụng cần phân phối vì nó phải chứa các bản sao đầy đủ của nhiều thư viện được liên kết tĩnh), nâng cấp (ứng dụng cần được biên dịch lại và liên kết lại mỗi khi có yêu cầu cần phải cập nhật thư viện)  

3. Liên kết động 

- ứng dụng sử dụng thư viện từ bên ngoài bằng cách sử dụng 'stubs' (điểm neo), thư viện được cài đặt trên hệ thống (HĐH) chính, nhưng không được cài đặt cùng với ứng dụng 

- Ưu điểm: 

	+ kích thước (ứng dụng nhỏ hơn vì các thư viện tách biệt với nó), nâng cấp (không cần biên dịch lại hoặc liên kết lại khi/nếu thư viện được cập nhật)

### ld.so 

• Mỗi khi một ứng dụng cần sử dụng một thư viện chia sẻ, dịch vụ ld.so được gọi 

• Còn được gọi là 'dynamic linker' (bộ liên kết động)  

### ldd [tên_file]  

- Hiển thị danh sách tất cả các thư viện mà ứng dụng thực thi động đã được chỉ định yêu cầu (và xem xét xem chúng có hiện diện không).

### ldconfig  

- Cấu hình các liên kết chạy thời gian của bộ liên kết động (tạo liên kết và lưu vào bộ nhớ cache các thư viện chia sẻ mới nhất được tìm thấy).

- Tìm kiếm theo những gì được chỉ định trên dòng lệnh. 

- Tìm kiếm theo những gì được chỉ định trong file ld.so.conf  

- Tạo ra file /etc/ld.so.cache, một tệp nhị phân liệt kê các thư viện trên hệ thống như phát hiện được (được sử dụng bởi ld.so khi cần thiết). 

- Thường chạy sau khi cập nhật hệ thống (tự động hoặc thủ công) hoặc sau khi càt đặt ứng dụng bên thứ ba (có thể đã thêm các thư viện).  

### /etc/ld.so.conf 

- Danh sách tiêu chuẩn các vị trí file thư viện được liệt kê trong file này.

- Lưu ý: Nếu có một dòng tồn tại `include ld.so.conf.d/*.conf`, nó cũng sẽ đọc tất cả các files được chỉ định, tìm kiếm các thư viện trong những vị trí đó (phương pháp mới hơn)  

- Định dạng các mục đơn giản là đường dẫn đến thư mục mà bộ liên kết cần quét 
    
- Ví dụ:

    ```sh
	/usr/lib/qt-3.3/lib
	```

### LD_LIBRARY_PATH  

- Một biến môi trường có thể chỉ định cho người dùng hoặc toàn bộ hệ thống, xác định một đường dẫn (theo định dạng thông thường, được phân tách bằng dấu hai chấm (:)), mà các ứng dụng ld.so và ldconfig có thể tìm kiếm thư viện  

- Ví dụ:

```sh
export LD_LIBRARY_PATH=/opt/myapp/lib:/opt/anotherapp/lib  
```

- Sẽ tạo ra một biến môi trường phiên làm việc khi được thực thi trên dòng lệnh cho phép ldconfig tìm thấy các thư viện trong các đường dẫn đã chỉ định (ngoài các giá trị trong `/etc/ld.so.conf`)    
