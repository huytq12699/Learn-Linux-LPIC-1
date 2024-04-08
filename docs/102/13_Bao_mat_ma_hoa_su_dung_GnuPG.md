# Sử dụng GnuPG để mã hóa và giải mã files

### gnupg

- GnuPG Privacy Guard  

- Tạo khóa công khai(public key) và khóa riêng(private key) để mã hóa dữ liệu

### gpg

- Công cụ làm việc với các keys. 

- `--gen-key`

    + Sẽ yêu cầu bạn chọn loại khóa (RSA thường là mặc định)  
    
    + Theo các yêu cầu để cung cấp dữ liệu trong quá trình tạo cặp keys của bạn.  

- `Entropy`: "hạt giống" được sử dụng để tạo ra keys mã hóa, nó liên quan đến tính ngẫu nhiên của một số sự kiện trên HĐH Linux của bạn (việc tạo nó đúng cách có thể mất thời gian lớn đối với các khóa lớn).

    + Tạo entropy (Thử để testing)

    ```sh
         yum install rngd-tools

         rngd -r /dev/urandom 
        ```
- `-a`: Tạo public key dạng văn bản để cung cấp

- `-o [filename]`: file đầu ra

    + Lưu ý : 

    	+ Khi tạo keys, hãy chắc chắn rằng bạn đã đăng nhập vào hệ thống trực tiếp với tên người dùng và mật khẩu hoặc môi trường hoặc GPG sẽ không được cài đặt mà không cần cấu hình thủ công.

  		+ Khi hoàn thành, tên key sẽ được liệt kê trên đầu ra hiển thị lên màn hình, CHÚ Ý giá trị đó.  

- `--import [key]`: Nhập key được chỉ định (public key từ người sẽ gửi file cho bạn)  

- `--list-keys`: Liệt kê tất cả các keys đã nhập của bạn

### Mã hóa một file để gửi cho người dùng khác 

- Nhập file public key từ người nhận dự định sẽ gửi file mã hóa cho người này 

- Giải mã file bằng cách sử dụng khóa đã nhập và passphrase cần thiết

    + Ví dụ: gpg file.gpg  
        
        + Sẽ giải mã file với điều kiện đã nhập đúng key và bạn có mật khẩu passphrase được  
           tạo ra cùng với nó 