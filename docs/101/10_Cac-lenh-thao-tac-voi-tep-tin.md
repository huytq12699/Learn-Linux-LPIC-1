# Các lệnh thao tác với tập tin

## Lệnh cơ bản

- `# ls`: Xem danh sách các file và thư mục hiện hành

- `# ll`: Xem danh sách các file và thư mục hiện hành chi tiết

- Chuyển thư mục (change directory): `# cd`

	+ `cd /etc/selinux`: Chuyển tới thư mục selinux

	+ `cd`: Chuyển về thư mục chính của người dùng

	+ `cd A && ls`: Chuyển tới thư mục A và hiển thị danh sách file và các thư mục của nó

	+ `cd ..`: Chuyển về thư mục cha của thư mục hiện tại

- Tạo 1 thư mục mới: `# mkdir <ten_thu_muc>`

- Tạo 1 tập tin: `# touch <ten_tap_tin>`

- Tạo 1 tập tin dạng text: `# echo "" >> ~/<ten_tap_tin>`

- Mở tập tin: `# cat <tap_tin>` hoặc `# tail <tap_tin>`

## Lệnh xóa

- Xóa tập tin: `# rm`

	+ `# rm <ten_tap_tin>`: Xóa 1 tập tin

	+ `# rm <tap_tin_1> <tap_tin_2>`: Xóa nhiều tập tin

	+ `# rm /a/b/c/<tap_tin>`: Xóa tập tin theo đường dẫn

	+ `# rm -i`: Xóa có xác nhận lại

	+ `# rm -f`: Xóa không xác nhận

	+ `# rm -I <ten_thu_muc>/file*`: Xóa hàng loạt file có cấu trúc file[...]

- Xóa thư mục: `# rmdir`

	+ `# rmdir <ten_thu_muc>` hoặc `# rm -d`: Xóa 1 thư mục rỗng

	+ `# rm -r <ten_thu_muc>`: Xóa thư mục chứa các thư mục con và tập tin (có xác nhận cho từng đối tượng)
		
	+ `# rm -rf <ten_thu_muc>`: Xóa thư mục chứa các thư mục con và tập tin (không xác nhận)

## Lệnh Copy 

- Copy file: `# cp`

1. Copy file A thành file B tại thư mục hiện hành.

	Ví dụ:

	```sh
	cp A.txt B.txt 
	```

2. Copy nhiều file vào 1 thư mục khác. 

	Ví dụ: Copy file `A.txt, B.txt, C.txt, D.exe, E.exe` vào thư mục `huy` vừa tạo

	```sh
	mkdir huy
	touch ./{A,B,C}.txt
	touch ./{D,E}.exe
	cp A.txt B.txt C.txt D.exe E.exe huy/
	```
3. Copy file từ thư mục này sang thư mục khác. 

	Ví dụ: Copy file `A.txt` từ thư mục `huy` sang thư mục B

	```sh
	mkdir B
	cp /huy/A.txt B
	```
4. Xem thông tin copy, thêm `-v`. 

	Ví dụ:

	```sh
	cp -v A.txt B.txt C.txt D.exe E.exe huy/
	"A.txt" -> "huy/A.txt"
	"B.txt" -> "huy/B.txt"
	"C.txt" -> "huy/C.txt"
	"D.exe" -> "huy/D.exe"
	"E.exe" -> "huy/E.exe"
	```
5. Giữ nguyên thuộc tính file khi copy, thêm `-p`. 
Các thuộc tính giữ nguyên là: access time, modification date, user ID, group ID, file flag, file mode, access control lists.

	```sh
	cp -p /huy/A.txt B
	```

6. Copy thư mục: tương tự file. Ta thêm `-a` hoặc `-r`

	+ `-r`: Copy toàn bộ thư mục hoặc file con của thư mục được copy

	+ `-a`: Bao gồm option `-r` và thực hiện duy trì các thuộc tính của file hoặc folder như file mode, ownership, timestamps...

7. Copy không cho ghi đè: `-n`

8. Copy cho ghi đè không cần xác định: `-f`

9. So sánh 2 tệp tin hoặc 2 thư mục: `diff`

	```sh
	diff -c a.txt b.txt
	```