# Cài đặt KVM

Để cài đặt và sử dụng KVM trên một hệ thống Linux, bạn cần thực hiện các bước sau:

1. Kiểm tra hỗ trợ ảo hóa: Trước tiên, bạn cần kiểm tra xem CPU của máy tính hỗ trợ ảo hóa hay không? Điều này có thể được thực hiện bằng cách chạy lệnh sau trong terminal

```sh
	egrep -c '(vmx|svm)' /proc/cpuinfo
```
- Nếu đầu ra của lệnh là một số lớn hơn 0, điều đó có nghĩa là CPU hỗ trợ ảo hóa. Nếu không, bạn có thể cần phải kích hoạt tính năng ảo hóa trong BIOS của máy tính.

2. Cài đặt KVM và các gói liên quan

- Trên các hệ thống Linux phổ biến như Ubuntu hoặc CentOS, bạn có thể cài đặt KVM và các gói liên quan thông qua gói quản lý gói của hệ điều hành. Dưới đây là cách cài đặt trên Ubuntu và CentOS

+ Ubuntu:

```sh
	sudo apt update
	sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
```

+ CentOS:

```sh
	sudo yum install qemu-kvm libvirt virt-install bridge-utils
```

3. Kiểm tra và khởi động dịch vụ libvirt

- Trên Ubuntu:

```sh
	sudo systemctl status libvirtd
	sudo systemctl start libvirtd
	sudo systemctl enable libvirtd
```

- Trên CentOS:

```sh
	sudo systemctl status libvirtd
	sudo systemctl start libvirtd
	sudo systemctl enable libvirtd
```

4. Cấu hình mạng (tùy chọn)

- Nếu bạn muốn sử dụng mạng bridge cho các máy ảo của mình, bạn cần cấu hình mạng bridge trên hệ thống của bạn. Hướng dẫn cấu hình này có thể thay đổi tùy theo phiên bản và cài đặt của hệ điều hành, vì vậy bạn nên tìm hiểu cách cấu hình mạng bridge cho phiên bản cụ thể của mình.

5. Tạo và quản lý máy ảo 

- Sau khi cài đặt KVM, bạn có thể sử dụng các công cụ như `virt-manager`, `virsh`, hoặc `virt-install` để tạo và quản lý các máy ảo của mình. Các công cụ này cung cấp giao diện đồ họa hoặc dòng lệnh để bạn có thể tạo, khởi động, tắt và quản lý máy ảo.