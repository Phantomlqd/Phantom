#I. Đi sâu tìm hiểu file cấu hình apache
##Tổng quan các file trong apache

Hệ thống file của apache là một hệ thống phân cấp, nằm trong folder /etc/apache2. Bao gồm các file text và một số thư mục.
Dùng lệnh ls -F để xem tất cả các file

![](https://cloud.githubusercontent.com/assets/14356333/10543114/c7cea414-7446-11e5-94fc-0a704d34488d.jpg) 

###apache2.conf 
Đây là file cấu hình chính cho các máy chủ. Hầu như tất cả các cấu hình có thể được thực hiện từ bên trong tập tin này, mặc dù nó được khuyến khích để sử dụng riêng biệt, các tập tin được chỉ định được làm cho đơn giản. Tập tin này sẽ cấu hình mặc định và là điểm truy cập trung tâm cho máy chủ để đọc thông tin cấu hình chi tiết.

###ports.conf
Fie này được sử dụng để xác định rõ các cổng mà các virtual host lắng nghe. Hãy đảm bảo cấu hình đúng các file này nếu bạn muốn cấu hình SSL.

###conf.d/
Thư mục này được sử dụng để điều khiển mọi khía cạnh cụ thể của sự cấu hình apache. Ví dụ: nó thường được dùng để xác định cấu hình SSL và các lựa chọn bảo mật mặc định. 

###sites-available/
Thư mục này bao gồm các virtual host dùng để xác định các website khác nhau. Nó sẽ thiết lập nội dung nào được phục vụ cho những yêu cầu nào. Nó là những cấu hình sẵn có và những cấu hình chưa có hiệu lực.

###sites-enabled/
Thư mục này thiết lập virtual host nào đang được sử dụng. Thông thường, thư mục này gồm có các biểu tượng liên kết đến các file được xác định trong thư mục sites-available/ .

###mods-[enabled,available]/
Những thư mục này có cùng chức năng với các thư mục sites-available/ và sites-enabled/, nó xác định rõ các module có thể được thay thế tùy ý.

###magic 
File thiết lập của module mod_mime_magic trên Apache.

###envvars
File thiết lập các biến với giá trị sẵn để sử dụng trong các file cấu hình.

##Chi tiết các file trong apache
###apache2.conf
Đây là file lưu trữ cấu hình chi tiết chính cho máy chủ apache.

File này được chia làm 3 phần: configuration for the global Apache server process, configuration for the default server, and configuration of Virtual Hosts.

Trong Ubuntu và Debian, phần lớn các file là sự định nghĩa toàn cục và các default server và các virtual host được xử lí cuối cùng bằng các chỉ thị include.

Chúng ta có thể xem các chỉ thị include bằng cách kéo xuống phần dưới của file này nơi có rất nhiều các chỉ thị include.

Chúng ta sẽ tập trung vào các phần đầu tiền của file này để biết được cách mà Apache xác định các tùy chỉnh toàn cục của nó.

###Khu vực Global Configuration
Phần này được sử dụng để cấu hinhd một số tùy chỉnh điều khiển các mà apache hoạt động. Phần này sẽ có một số tùy chỉnh thú vị nếu bạn muốn sửa đổi.

####Timeout
Thông số này được mặc định là 300. Nghĩa là server sẽ có tối đa 300 giây để thực hiện yêu cầu.

Đây là ngưỡng thời gian quá lâu, bạn có thể chỉnh xuống tầm 30 đến 60.

####Keepalive
Nếu để on thì sẽ duy trì kết nối để thực hiện nhiều yêu cầu từ client.

Nếu để off thì mỗi yêu cầu từ phía client sẽ tạo một kết nối mới.

####MaxKeepAliveRequests
Xác định cụ thể số yêu cầu trong 1 phiên kết nối. Để 0 khi muốn vô số yêu cầu trong 1 phiên kết nối.

####KeepAliveTimeout
Chỉ số này xác định thời gian chờ đến yêu cầu tiếp theo sau khi yêu cầu trước đã kết thúc.

###MPM Configuration
Khu vực tiếp theo chỉ rõ những cấu hình của các tùy chọn MPM (Multi-Processing Module). Chúng ta có thể kiểm tra khu vực nào của apache đã được biên dịch bằng câu lệnh **apache2 -l**

![](https://cloud.githubusercontent.com/assets/14356333/10549599/442776ba-746c-11e5-978e-7b2156702560.jpg)

####Tìm hiểu các file virtual host mặc định
Sự khai báo virtual host mặc định có thể được tìm thấy trong các file **default** trong thư mục **sites-available**.

Chúng ta có thể biết được định dạng tổng quát của file virtual host bằng cách kiểm tra file này bằng lệnh **sudo vi /etc/apache2/sites-available/000-default.conf**.

![](https://cloud.githubusercontent.com/assets/14356333/10556776/6f44395e-74b8-11e5-9850-d145e6fa5d60.jpg)

File virtual host được cấu hình để xử lí các yêu cầu từ cổng 80 - chuẩn cho cổng http được mặc định ở phần header **<Virtual Host *:80>**.

Điều này không có nghĩa là apache nhất thiết phải xử lí yêu cầu trên cổng này. Apache sẽ sư dụng các virtual host khác nhau để xử lí từng yêu cầu khác nhau.

**ServerAdmin** xác định email liên lạc sẽ được sử dụng khi server gặp vấn đề.

**DocumentRoot** chứa nội dung của virtual host, được lưu ở thư mục **/var/www**

#II. Nguyên tắc xử lý của web server

![](https://cloud.githubusercontent.com/assets/14356333/10562301/263f9e56-7580-11e5-8ce1-7f3f382fefbe.gif)

Theo mô hình trên, trình duyệt web (bên trái) thực hiện một kết nối tới máy chủ web (bên phải), yêu cầu một trang web và nhận lại nó. Sau đây, là thứ tự từng bước cơ bản xảy đến đằng sau màn hình của bạn:

Trình duyệt web tách địa chỉ website làm 3 phần:

Tên giao thức: “http”

Tên miền của máy chủ web: “http://xxx.com”

Tên tệp HTML: “yyy.htm”

Trình duyệt liên hệ với máy chủ tên miền (DNS Server) để chuyển đổi tên miền “http://xxx.com” ra địa chỉ IP tương ứng. Sau đó, trình duyệt sẽ gửi tiếp một kết nối tới máy chủ của website có địa chỉ IP này qua cổng 80. Dựa trên giao thức HTTP, trình duyệt gửi yêu cầu GET đến máy chủ, yêu cầu tệp HTML “web-server.htm”. (Chú ý: một cookies cũng sẽ được gửi kèm theo từ trình duyệt web đến máy chủ).

Tiếp đến, máy chủ sẽ gửi một file văn bản có các thẻ HTML đến trình duyệt web của bạn (một cookies khác cũng được gửi kèm theo từ máy chủ tới trình duyệt web, cookies này được ghi trên đầu trang của mỗi trang web).

Trình duyệt web đọc các thẻ HTML để xác lập định dạng (hình thức trình bày) trang web và kết xuất nội dung trang ra màn hình của bạn.

#III. Các module cơ bản trong apache

##Chuyển đổi giữa URI thành filename trên server

Mod_userdir: chuyển thư mục home cho từng user.

Mod_rewrite: điều chỉnh lại đường dẫn URL.

##Giai đoạn Xác thực / phân quyền

mod_auth, mod_auth_anon,mod_auth_db, mod_auth_dbm: các kiểu xác thực người dùng.

Mod_access: kiểm soát truy nhập theo từng host.

##Xác định MIME của đối tượng được truy vấn

mod_mime: xác định loại file bằng cách dựa vào phần mở rộng.

mod_mime_magic: xác định loại file bằng cách sử dụng “magic number”

##Chỉnh sửa đường dẫn

Mod_alias: thay thế alias bằng đường dẫn thực trên server.

Mod_env: thay đổi các tham số hệ thống dựa trên thông tin trong file cấu hình.

Mod_spelling: tự động sửa lỗi trong URL.

##Gửi trả lại dữ liệu cho client

Mod_actions: các script cho từng loại file sẽ được thực thi.

Mod_asis: gửi file nguyên dạng

Mod_autoindex:


Mod_cgi: gọi script CGI và trả lại kết quả.

Mod_include:

Mod_dir: xử lý về thư mục

Mod_imap: xử lý image-map files.

##Ghi log

Mod_log_*: các module log khác nhau.

##Các module quan trọng đối với Apache Server

httpd_core: Chứa các chức năng cốt lõi của Apache, cần thiết cho bất cứ Apache nào.

mod_access: Cung cấp chế độ khiển tác dựa trên tên máy, địa chỉ IP, hoặc các tính chất yêu cầu thuộc về các clients. Bởi vì module này cần cho các chỉ phối (directive) “order”, “allow” và “deny”, nó cần được cho phép.

mod_auth: Cần thiết để ứng dụng vấn đề khai báo người dùng cho việc sử dụng các hồ sơ nguyên bản (khai báo căn bản cho HTTP), được chỉ định trong chức năng trù bị.

mod_dir: Cần thiết để tìm kiếm và phục vụ các hồ sơ thư mục: “index.html”, “default.htm”, v..v..

mod_log_config: Cần thiết để ứng hiệu báo cáo những yêu cầu thực hiện đến server.

mod_mime: Cần thiết để chỉnh lý nhóm chữ cái, mã hoá nội dung, tùy tác ngôn ngữ nội dung và các loại MIME đại diện cho các loại tài liệu.

Module httpd_core

Module này đóng vai trò đảm nhiệm các chức năng chính của Web Server. Các 

##Directive bao gồm:

DefaultType

DocumentRoot

 MaxClients

Modules

Port

ServerAdmin

ServerName

ServerRoot

SocketType

SSLCertificateFile

SSLCertificateKeyFile

SSLVerifyClient

#IV. Name-based và IP-based
##Name-based
Đối với name-based chúng ta có thể cài đặt nhiều tên miền trên cùng 1 IP. Chúng chỉ phải cấu hình DNS của tên miền để khớp với IP sau đó cấu hình apache để nó nhận ra tên miền.

##IP-based
Đối với IP-based chúng ta có thể cài đặt mỗi IP cho mỗi tên miền khác nhau, các IP này sẽ được đính kèm đến mỗi server cùng với mỗi card mạng khác nhau.

#V. Virtual Host
Thư mục /var/www/html để chứa dữ liệu website gốc thì virtual host giúp chúng ta thiết lập một website ảo.

Đầu tiên chúng ta cần tạo ra một thư mục để chứa dữ liệu tập tin của trang web. Vì apache mặc định dùng tập tin /var/www nên ta tạo ra một tập tin **kma.com** trong này có chứa file sẽ chứa dữ liệu của trang web là **ubuntu_html**

![](https://cloud.githubusercontent.com/assets/14356333/10564674/79eb84e6-75e6-11e5-94ef-0c23b425456b.jpg)

Trong ubuntu cấu hình virtual host nằm trong tập tin **/etc/apache2/sites-available**. Chúng ta sẽ thấy 2 virtual host mặc định là **000-default.conf** và **default-ssl.conf**. Ta sẽ tạo 1 file virtual host khác là **kma.com.conf** rồi copy nội dung của thư mục virtual host mặc định là **000-default.conf** sang.

![](https://cloud.githubusercontent.com/assets/14356333/10564748/ac852e2c-75e9-11e5-8a17-8c3f64131ebb.jpg)

Mở và chỉnh sửa tập tin **/etc/apache2/sites-available/kma.com.conf**

- ServerName: ở đây cần sửa lại thành domain là **ubuntu.com**, bỏ dấu # đi.

- ServerAdmin: email của chúng ta cho domain này

- DocumentRoot: đây là thư mục sẽ lưu trữ trang web mà chúng ta đã tạo ở trên, như ví dụ ở trên là **/var/www/vidu1.com/ubuntu_html**

- ServerAlias: mặc định sẽ không có mục này. Tuy nhiên bạn có thể thêm nó ở phía dưới ServerName. Thông số này giống như Parked domain hay CNAME vậy.

![](https://cloud.githubusercontent.com/assets/14356333/10564967/f723ae4e-75ef-11e5-8b90-0c98c62ab914.jpg)

Bật virtual host và khởi động lại

![](https://cloud.githubusercontent.com/assets/14356333/10564795/75f6a5be-75eb-11e5-89b0-60a64bdc9f87.jpg)

Để kiểm tra việc thiết lập virtual host ta tạo 1 file **index.html** trong thư mục **/etc/apache2/kma.com/ubuntu_html**.

![](https://cloud.githubusercontent.com/assets/14356333/10564875/4dfa4802-75ed-11e5-988b-590a6fcf4f70.jpg)

Sau đó chỉnh sửa file host để IP trỏ về trang web.

![](https://cloud.githubusercontent.com/assets/14356333/10564916/3c3ab466-75ee-11e5-87f4-68f16f098b76.jpg)
