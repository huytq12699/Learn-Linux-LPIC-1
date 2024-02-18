# Lệnh nén và giải nén trong Linux

- Các option dùng với lệnh `tar`
	+ `-c`: Tạo file nén.tar

	+ `-x`: Giải file nén .tar

	+ `-v`: Hiển thị quá trình nén và giải nén dữ liệu ra màn hình

	+ `-f`: Chỉ định nén thành file

	+ `-t`: Xem dữ liệu trong file nén

	+ `-j`: Tạo file nén với bzip2 có định dạng file.tar.bz2

	+ `-z`: Tạo file nén với gzip có định dạng file.tar.gz

	+ `-r`: Thêm một file và thư mục vào file nén đã tồn tại

	+ `--wildcards`: Tìm và xuất file bất kỳ trong file nén

# Các lệnh nén
- Nén file/thư mục sang định dạng "tar": `# tar -cvf`
	+ `# tar -cvf filenenA.tar /mnt/A` : Nén thư mục `A` thành `filenenA.tar` và show quá trình nén

- Nén file/thư mục sang định dạng "tar.gz": `# tar -cvzf`
	+ `# tar -cvfz filenenA.tar.gz /mnt/A`: Nén thư mục `A` thành `filenenA.tar.gz` và show quá trình nén

# Các lệnh giải nén
+ `tar -xvf filenenA.tar /mnt/A`

+ `tar -xvfz filenenA.tar.gz /mnt/A`

+ `tar -xvfj filenenA.tar.bz2 /mnt/A`

# Thêm file và folder vào file nén

- Thêm file `abc.txt` vào `filenenA.tar`
	+ `# tar -rvf filenenA.tar abc.txt`

- Thêm thư mục `A` vào `filenenA.tar`
	+ `# tar -rvf filenenA.tar A`



