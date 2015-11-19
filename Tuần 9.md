#1. Viết script cài đặt wordpress trên ubuntu server:
    #!/bin/bash
	read software;
	apt-get install $software;
Đầu tiên tạo 1 file có tên tùy ý, ở đây mình đặt là **install.sh**

![](https://cloud.githubusercontent.com/assets/14356333/11275584/da83cec4-8f10-11e5-95da-de50d2931cae.png)

Sau đó dùng câu lệnh **read** để nhập tên gói muốn cài đặt, lệnh thứ 2 dùng để cài đặt gói có tên vừa nhập

![](https://cloud.githubusercontent.com/assets/14356333/11275690/710ea29c-8f11-11e5-9590-a1c31c98ff5d.png)

Tiếp theo, cấp quyền cho file vừa tạo rồi chạy như bình thường. Nhập tên gói muốn cài, hệ thống sẽ tự động cài đặt gói bạn cần.
#2. Tìm hiểu giao thức SSH
SSH (tiếng Anh: Secure Shell) là một giao thức mạng dùng để thiết lập kết nối mạng một cách bảo mật. SSH hoạt động ở lớp trên trong mô hình phân lớp TCP/IP. Các công cụ SSH (như là OpenSSH,...) cung cấp cho người dùng cách thức để thiết lập kết nối mạng được mã hoá để tạo một kênh kết nối riêng tư. Hơn nữa tính năng tunneling của các công cụ này cho phép chuyển tải các giao vận theo các giao thức khác. Do vậy có thể thấy khi xây dựng một hệ thống mạng dựa trên SSH, chúng ta sẽ có một hệ thống mạng riêng ảo VPN đơn giản.

SSH là một chương trình tương tác giữa máy chủ và máy khách có sử dụng cơ chế mã hoá đủ mạnh nhằm ngăn chặn các hiện tượng nghe trộm, đánh cắp thông tin trên đường truyền. Các chương trình trước đây: telnet, rlogin không sử dụng phương pháp mã hoá. Vì thế bất cứ ai cũng có thể nghe trộm thậm chí đọc được toàn bộ nội dung của phiên làm việc bằng cách sử dụng một số công cụ đơn giản. Sử dụng SSH là biện pháp hữu hiệu bảo mật dữ liệu trên đường truyền từ hệ thống này đến hệ thống khác.

##Cách thức làm việc của SSH

SSH làm việc thông qua 3 bước đơn giản:

Định danh host - xác định định danh của hệ thống tham gia phiên làm việc SSH.

Mã hoá - thiết lập kênh làm việc mã hoá.

Chứng thực - xác thực người sử dụng có quyền đăng nhập hệ thống.

##Demo cấu hình SSH
https://www.youtube.com/watch?v=FUWXRI5k-hg
