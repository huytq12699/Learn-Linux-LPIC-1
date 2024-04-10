# File Permissions

- Trong Linux mọi tệp đều liên kết với người dùng là chủ sở hữu. Mỗi tệp cũng được liên kết với 1 nhóm có 
liên quan đến tệp và các quyền hoặc quyền nhất định: đọc, viết, thực thi...

- Các tệp có 3 loại quyền: đọc(r), ghi(w), thực thi(x). 3 quyền này được đại diện theo thứ tự: Người dùng (User), 
Nhóm (group), Người dùng khác (other user).

|rwx: |rwx: |rwx:|
|---|---|---|
|u: |g:|o:|


# Giải thích ý nghĩa

- `rwx`: Là quyền của User. Ở đây User có đầy đủ 3 quyền là read (đọc), write (ghi) và excute (thực thi)

- `r-x`: Là quyền của Group. Ở đây Group có 2 quyền là read (đọc) và excute (thực thi)

- `r-x`: Là quyền của các User khác. Ở đây các User khác có 2 quyền là read (đọc) và excute (thực thi)

- `root root`: Các quyền ở trên là quyền của User root và Group root

- `ls -lah`: Kiểm tra đầy đủ thông tin của một file (bao gồm quyền)

- `chmod`: Thay đổi quyền truy cập của người dùng tới file hoặc folder

- `chown`: Thay đổi quyền sở hữu của một file hoặc thư mục

- `chgrp` : Thay đổi quyền sở hữu nhóm(group) của một file hoặc thư mục

### Thay đổi quyền của file và folder

```sh
chmod [options] [mode] file1 file2 file3 ...
```
- Các options: 
	+ `-R`: Recursive, áp dụng cho tất cả các file và folder bên trong

	+ `-f`: force, thay đổi quyền trong cả trường hợp xảy ra lỗi

	+ `-v`: verbose, hiển thị đối tượng đã xử lý

- Các mode:

|#|Permission|rwx|
|-|----------|---|
|7|read (2^2), write (2^1) and execute (2^0)|rwx|
|6|read (2^2) and write (2^1)|rw-|
|5|read (2^2) and execute (2^0)|r-x|
|4|read (2^2) only|r--|
|3|write (2^1) and execute (2^0)|-wx|
|2|write (2^1) only|-w-|
|1|execute (2^0) only|--x|
|0|none|---|



