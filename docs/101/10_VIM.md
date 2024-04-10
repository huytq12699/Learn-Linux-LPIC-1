# VIM

## Khái niệm cơ bản

- Lệnh `vi/vim`  

- Một trình soạn thảo phổ biến có sẵn trong tất cả các bản phân phối Linux 

- Hoạt động trong ba chế độ riêng biệt:

	+ Chế độ lệnh - được sử dụng để di chuyển con trỏ và thực hiện các hoạt động khác nhau trên văn bản  

	+ Chế độ chèn - thêm/chèn văn bản vào tài liệu của bạn  

	- Chế độ Ex (hay LastLine) - chế độ nâng cao để tìm/thay thế, thực thi các lệnh bên ngoài và sử dụng các khung chia

## Một số lệnh cấu hình

- `/etc/vimrc`: File cấu hình vim toàn cầu 

- `/home/user/.vimrc`: Cấu hình cụ thể cho người dùng của vim

- Vim sẽ bắt đầu ở chế độ 'command' (lệnh)     

- `# vi <ten_file>`. Nếu file chưa tồn tại thì hệ thống sẽ tạo ra file đó.

- Nhấn phím `i` (Insert): Để chỉnh sửa văn bản

- Nhấn phím `ESC` để thoát khoải trạng thái nhập

- `:wq`: Thoát và lưu lại file sửa đổi 

- `:q!`: Để thoát mà không lưu

- `I`: di chuyển đến đầu dòng hiện tại và chuyển sang 'insert mode'

- `a` : chuyển sang chế độ 'insert mode', đặt con trỏ một ký tự sang phải so với vị trí hiện tại (append)  

- `A` : di chuyển đến cuối dòng hiện tại, đặt con trỏ một ký tự sang phải so với vị trí cuối (line append)  

- `o`: chèn một dòng mới dưới dòng hiện tại, đặt con trỏ ở vị trí đầu tiên trên dòng mới trong chế độ 'insert mode'  

- `O`: chèn một dòng mới phía trên dòng hiện tại, đặt con trỏ ở vị trí đầu tiên trên dòng mới trong chế độ 'insert mode' 

- `c[tùy chọn]`: thay đổi văn bản tại vị trí hiện tại 

- `cw`: thay đổi từ hiện tại tại vị trí con trỏ  

- `cc`: thay đổi dòng hiện tại tại vị trí con trỏ  

- `c$`: thay đổi từ vị trí hiện tại đến cuối dòng  

- `r`:thay thế ký tự tại vị trí hiện tại  

- `R`: thay thế văn bản trên cùng một dòng cho đến khi thoát khỏi chế độ 'insert mode' hoặc đến cuối dòng  

- `x`: xóa ký tự sau con trỏ  

- `X`:xóa ký tự trước con trỏ  

- `dw`: xóa từ sau con trỏ  

- `dd`: xóa toàn bộ dòng mà con trỏ đang đứng trên đó  

- `D`: xóa văn bản từ vị trí con trỏ đến cuối dòng  

- `dL`: xóa văn bản từ vị trí con trỏ đến cuối màn hình hiện tại  

- `dG`: xóa văn bản từ vị trí con trỏ đến cuối file  

- `d^`: xóa toàn bộ văn bản từ đầu dòng đến vị trí con trỏ hiện tại

- `u`: hoàn tác thao tác/thay đổi cuối cùng  

- `yy`: sao chép dòng hiện tại vào bộ đệm (thường được gọi là yank) 

- `yw`: sao chép từ vị trí con trỏ hiện tại đến cuối từ hiện tại  

- `p`: dán nội dung của bộ nhớ đệm sau con trỏ  

- `P`: dán nội dung của bộ nhớ đệm trước con trỏ  

- `:e!`: hoàn tác TẤT CẢ các thay đổi kể từ lần cuối cùng file được lưu vào đĩa  

- `:w`: lưu tệp xuống đĩa (lưu lại)

### Tìm kiếm 

- Phải ở chế độ lệnh (nhấn phím `ESC` để chắc chắn đang ở chế độ lệnh) 

- `:<so_dong>`: Để chuyển đến dòng muốn tìm kiếm.

- `/<tu_muon_tim_kiem>`: Để tìm kiếm từ trong file file đó.

- `/[chuỗi]`: tìm kiếm từ vị trí con trỏ trở đi cho 'chuỗi'

- `?[chuỗi]`: Tìm kiếm từ vị trí con trỏ ngược lại cho 'chuỗi'

- `N`: khi được sử dụng sau một tìm kiếm, sẽ tìm kiếm 'tiếp theo' sự xuất hiện của 'chuỗi' trong hướng được chỉ định

### Phím tắt di chuyển

- `h`: di chuyển một ký tự sang trái

- `j`: di chuyển một dòng xuống

- `k`: di chuyển một dòng lên

- `l`: di chuyển một ký tự sang phải

- `ctl-u`: di chuyển lại một nửa trang

- `ctl-b`: di chuyển lại một trang

- `ctl-d`: di chuyển tiếp một nửa trang

- `ctl-f`: di chuyển tiếp một trang

- `ctl-G`: hiển thị tên file, số dòng và vị trí theo phần trăm so với tổng độ dài file

- `[#]G`: di chuyển trực tiếp đến dòng được chỉ định

- `[#]W`: di chuyển 12 từ sang phải

### Thay thế

- Phải ở chế độ lệnh (nhấn phím `ESC` để chắc chắn đang ở chế độ lệnh)

- Cú pháp tương tự như sed  

- `s`: thay thế (trong dòng hiện tại)  

- `%s`: thay thế (trong toàn bộ file)  

- `/[giá trị cần tìm]`: giá trị cần tìm  

- `/[giá trị cần thay thế]/`: giá trị để thay thế  

- `g`: tùy chọn, sẽ thay thế TẤT CẢ các sự xuất hiện thay vì chỉ sự xuất hiện đầu tiên             