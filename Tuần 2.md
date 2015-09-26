#Tìm hiểu cách sử dụng VMWare Workstation

##1. Giới thiệu:
VMWare là một phần mềm ảo hóa rất nổi tiếng. Nó có chức năng ảo hóa cài đặt các hệ điều hành khác nhau trên cùng một máy tính. Máy tính thật có thể chia sẻ tài nguyên phần cứng như ram, cpu, hard disk, ..... cho máy ảo. Các máy ảo có thể được liên kết với nhau tạo thành một mạng LAN ảo, thậm chí có thể kết nối đến máy tính vật lí hoặc kết nối internet ra bên ngoài. Đối với chuyên gia về mạng, hệ thống, VMWare giúp họ thiết lập được một môi trường mạng ảo để phân tích thiết kế hệ thống. Đối vơi các chuyên gia bảo mật, VMWare trợ giúp họ thiết lập môi trường mạng ảo để để kiểm thử xâm nhập (Penetration Testing), nghiên cứu bảo mật, nghiên cứu mã độc một cách an toàn (hiện nay tồn tại một số loại mã độc có khả năng xác định được đang chạy trong môi trường ảo, tìm cách lây lan ra máy tính thật). Đối với các nhà phát triển phần mềm, VMWare trợ giúp học trong việc kiểm tra việc vận hành các sản phẩm trên những nền tảng hệ điều hành khác nhau.

##2. Các chế độ card mạng trong VMWare:

![image](https://cloud.githubusercontent.com/assets/14356333/10108194/ba0c6fae-63e9-11e5-9f1f-7af48f024035.jpg)

- Bridge: card mạng ảo sẽ dùng chính card mạng của máy thật để kết nối ra internet.
- NAT: chia sẻ IP của máy thật để máy ảo có thể kết nối ra internet
- Host-only: kết nối với các máy ảo khác
(Chúng ta có thể thêm bớt các card mạng ảo ở 2 mục Add Network và Remove Network)

##3. Cách sử dụng và cài đặt Ubuntu Server 15.04:
![](https://cloud.githubusercontent.com/assets/14356333/10108653/6582e2a8-63ec-11e5-818d-84e1debca64b.jpg)

- Cài đặt xong chúng ta khởi động chương trình. Trong cửa sổ này có các tùy chọn:
	+ Create a New Virtual Machine: tạo một máy ảo mới
    + Open a Virtual Machine: khởi động một máy ảo đã cài sẵn
    + Connect a Remote Server: kết nối từ máy chủ
    + Connect to VMWare: kết nối từ đám mây
- Ở đây để tạo máy ảo mới ta chọn Create a New Virtual Machine.

![](https://cloud.githubusercontent.com/assets/14356333/10115324/7e8f1654-642d-11e5-82f0-4766fc6f4b7a.jpg)

- Có 2 lựa chọn:
   + Typical: cài máy ảo 1 cách đơn giản, cấu hình máy ảo sẽ do chương trình tự quyết định (có thể chỉnh lại sau).
   + Custom: cài máy ảo với những thiết lập về cấu hình ngay từ đầu.
 
- Ở đây chúng ta chọn Typical, click chuột vào next.

![](https://cloud.githubusercontent.com/assets/14356333/10115353/3f33dd36-642e-11e5-9387-7570afa9ea46.jpg)

- Chọn Installer disc nếu cài từ ổ đĩa máy tính, ở đây chúng ta chọn Installer disc image file (iso) vì đã có file iso của hệ điều hành.

- Chọn mục browse tìm đến file Ubuntu Server iso. Chọn next.

![](https://cloud.githubusercontent.com/assets/14356333/10115386/449967fe-642f-11e5-851f-6cd050e498a9.jpg)

- Điền tên, tài khoản người dùng và mật khẩu, chọn next.

![](https://cloud.githubusercontent.com/assets/14356333/10115403/0f9c2b8a-6430-11e5-9519-6c897f7fd4af.jpg)

- Đặt tên máy ảo, chọn đường dẫn cài đặt máy ảo, chọn next.

![](https://cloud.githubusercontent.com/assets/14356333/10115413/775fc5ec-6430-11e5-9ca0-e0d600293b1d.jpg)

- Tiếp theo chúng ta cài đặt dung lượng ổ cứng cho máy ảo, ở đây ta chọn 20GB.
- Có thêm 2 lựa chọn:
  + Store virtual disk as a single file: cài đặt máy ảo với một file duy nhât.
  + Store virtual disk into multiple files: cài đặt máy ảo chia nhỏ ra nhiều file.
Ở đây ta chọn Store virtual disk into multiple files.

![](https://cloud.githubusercontent.com/assets/14356333/10115421/f994277e-6430-11e5-9aa8-66930622329e.jpg)

- Chọn mục Customize Hardware để thiết lập lại cấu hình cho máy ảo. Sau đó chọn Finish để chương trình cài đặt hệ điều hành cho máy ảo. Tích vào ô Power on this virtual machine after creation để máy ảo tự khởi động luôn sau khi cài đặt xong.
