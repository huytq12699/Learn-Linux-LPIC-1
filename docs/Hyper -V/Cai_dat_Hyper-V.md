# Cài đặt Hyper -V trên Windows

1. Kiểm tra yêu cầu hệ thống:

- Hyper-V yêu cầu một bộ xử lý hỗ trợ ảo hóa, như Intel VT-x hoặc AMD-V.

- Cần kích hoạt tính năng ảo hóa trong BIOS của máy tính của bạn.

- Yêu cầu hệ điều hành Windows 10 Pro, Enterprise hoặc Education trở lên để cài đặt Hyper-V.

- Trên hệ điều hành Windows Server, Hyper-V có sẵn như một tính năng của Windows Server.

2. Cài đặt

- Bước 1: Mở `Control Panel (Bảng điều khiển)` bằng cách nhấn tổ hợp phím `Windows + R`, gõ `control panel` và nhấn `Enter`.

- Bước 2: Chọn `Programs(Chương trình)` > `Turn Windows features on or off (Bật hoặc tắt tính năng Windows)`.

- Bước 3: Trong hộp thoại `Windows Features`, tìm và chọn `Hyper-V`, sau đó nhấn `OK`.

- Bước 4: Một hộp thoại cảnh báo sẽ xuất hiện. Nhấn `Yes` để tiếp tục. Hệ thống có thể yêu cầu khởi động lại máy tính của bạn sau khi 
cài đặt hoàn tất.

3. Kiểm tra cài đặt

- Sau khi khởi động lại máy tính, bạn có thể mở `Hyper-V Manager` từ menu Start để quản lý các máy ảo của mình.

- Nếu `Hyper-V Manager` không xuất hiện trong menu Start, bạn có thể tìm kiếm nó trong `Cortana` hoặc 
mở nó từ `Run` (nhấn tổ hợp phím Windows + R và nhập "virtmgmt.msc").

- Sau khi hoàn thành các bước trên, bạn đã cài đặt thành công Hyper-V trên hệ điều hành Windows của mình và 
có thể bắt đầu tạo và quản lý các máy ảo.