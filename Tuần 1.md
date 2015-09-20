#Mô hình OSI
##I. Khái niệm:
- OSI là viết tắt của Open Systems Interconnection model- mô hình liên kết các hệ thống mở, còn được gọi là mô hình 7 tầng OSI. 
- Là mô hình khái niệm về sự định tính và chuẩn hóa các chức năng giao tiếp của một hệ thống viễn thông hoặc một hệ thống máy tính mà không cần quan tâm tâm đến cấu trúc bên trong và công nghệ.
- Nhiệm vụ của nó là đảm bảo khả năng tương tác và liên kết của các hệ thống truyền thông nó cấu trúc khác nhau bằng các giao thức tiêu chuẩn.
- Được xây dựng dựa trên cấu trúc phân tầng với 7 tầng liên kết với nhau có chức năng và nhiệm vụ khác nhau.

##II. Các tầng trong mô hình OSI
![image](https://upload.wikimedia.org/wikipedia/commons/d/d3/Osi-model-jb.png)
###1. Physical layer (tầng vật lí)
####1.1 Chức năng:
- Truyền nhận các dòng bit thô qua môi trường vật lí.
- Định nghĩa các đặc điểm về điện, vật lí của sự kết nối các dữ liệu.
- Định nghĩa mối quan hệ giữa các thiết bị với môi trường truyền nhận tín hiệu.
- Thiết lập và ngắt các kết nối giữa 2 nút qua môi trường truyền thông.
- Định nghĩa giao thức qua chế độ điều khiển luồng.
- Xác định chế độ truyền tín hiệu. VD: simplex, half duplex, full duplex.
- Xác định cấu trúc mạng, như: bus, star, ring.

####1.2 Đơn vị dữ liệu: bit.

####1.3 Các công nghệ:
- DSL, USB, ISDN

###2. Datalink layer (tầng liên kết dữ liệu)
####2.1 Chức năng:
- Đảm bảo sự truyền các khung dữ liệu một cách tin cậy giữa 2 nút mạng bởi tầng vật lí bằng cách phát hiện và sửa lỗi nếu có của tầng vật lí.
- Có thể chia làm 2 tầng nhỏ hơn bỏi chuẩn IEEE 802: MAC( media access control- điều khiển truy cập đường truyền) và LLC( Logical link control- điều khiển liên kết logic).
- Giao thức kết nối *điểm tới điểm* là một ví dụ cho tầng liên kết dữ liệu trong chồng giao thức TCP/IP.
 
####2.2 Đơn vị dữ liệu: bit hoặc frame.

####2.3 Các chuẩn: PPP, IEEE 802.2, L2TP, MAC.

###3. Network layer( tầng mạng)
####3.1 Chức năng:
- Cấu trúc hóa và quản lí các nút mạng bao gồm: cấp địa chỉ IP, định tuyến và điều khiển lưu lượng.
- Cung cấp các chức năng và thủ tục để truyền các gói tin có dung lượng khác nhau từ một nút mạng này tới một núc khác trong cùng một mạng.
- Cấp địa chỉ IP cho các nút mạng.
- Chuyển đổi địa chỉ logic thành địa chỉ vật lí.
- Tìm đường đi ngắn nhất để truyền các gói tin.

####3.2 Đơn vị dữ liệu: packet hoặc datagram

####3.3 Các giao thức: IPv4, IPv6, IPsec, AppleTalk, ICMP

###4. Transport layer( tầng giao vận)
####4.1 Chức năng:
- Cung cấp các chức năng và thủ tục cho việc truyền các gói dữ liệu từ nguồn tới đích qua 1 hay nhiều mạng mà vẫn đảm bảo chất lượng dịch vụ.
- Đảm bảo sự tin cậy của các liên kết đã được xác định qua cơ chế điều khiển luồng.
- Phân đoạn và khôi phục dữ liệu.
- Cung cấp cơ chế báo nhận dữ liệu.

####4.2 Đơn vị dữ liệu: segment
####4.3 Các giao thức: TCP, UDP, NETBEUI

###5. Session layer( tầng phiên):
####5.1 Chức năng:
- Thiết lập, quản lí, chấm dứt các phiên kết nối của các ứng dụng cục bộ hoặc ứng dụng ở xa.
- Tổ chức và điều phối các phiên giao tiếp giữa các hệ thống bằng các chế độ: full-duplex, half-duplex, or simplex.
- Cung cấp chế độ đánh đấu điểm hoàn thành (checkpointing) để phục hồi phiên truyền thông khi có lỗi xảy ra.

####5.2 Đơn vị dữ liệu: data

####5.3 Các giao thức: RPC, PAP, SSL, SQL

###6. Presentation layer( tầng trình diễn):
####6.1 Chức năng:
- Dịch dữ liệu từ tầng application vè dạng format.
Ở máy tính nhận thì ngược lại.
- Dịch các mã kí tự.
- Chuyển đổi dữ liệu.
- Nén dữ liệu.
- Mã hóa, giải mã dữ liệu

####6.2 Đơn vị dữ liệu: data

####6.3 Các công nghệ: HTML, CSS, GIF

###7. Application layer( tầng ứng dụng):
####7.1 Chức năng:
- Là tầng gần với người sử dụng nhất.
- Cung cấp phương tiện cho người dùng truy cập thông tin và dữ liệu qua các phần mềm ứng dụng.

####7.2 Đơn vị dữ liệu: data

####7.3 Các dịch vụ: HTTP, FTP, SMTP, SSH, TELNET

##III. Ưu điểm:
- Giảm thiểu độ phức tạp.
- Chuẩn hóa các giao diện.
- Tạo điều kiện thuận lợi cho việc mô đun hóa.
- Đảm bảo khả năng tương thích giữa các nhà phân phối.
- Đảm bảo sự tương thích về mặt công nghệ.
- Thúc đẩy sự phát triển công nghệ mạng.
- Đơn giản hóa việc dạy và học.

#TCP/IP
##I. Khái niệm
- Là một mô hình mạng máy tính và bộ giao thức truyền thông sử dụng trên internet và các mạng máy tính độc lập.
- Là bộ giao thức được sử dụng phổ biến nhất trên thế giới.
- Được chia thành 4 tầng với chức năng và nhiệm vụ khác nhau.
- Các tầng trên càng gần với người dùng hơn ngược lại là các tầng dưới càng gần với việc truyền dữ liệu và vật lí.

##II. Các tầng trong mô hình TCP/IP
![TCP/IP](http://www.cellbiol.com/bioinformatics_web_development/lib/exe/fetch.php/chapter_1_-_internet_networks_and_tcp-ip/tcp-ip_layers.png?cache=)

###1. Network interface layer( tầng giao diện mạng)
####1.1 Chức năng
- Bao gồm cả 2 tầng vật lí và liên kết dữ liệu so với mô hình OSI.
- Có nhiệm vụ chuyển các gói tin từ tầng mạng tới các máy chủ khác nhau.
- Còn có thể là nơi các gói tin được chặn để gửi qua một mạng riêng ảo.
- Là nơi kết hợp của các thành phần vật lí như: hub, các bộ lặp (repeater), cáp mạng, cáp quang, cáp đồng trục (coaxial cable), card mạng... các đặc tả mức thấp về các tín hiệu (mức hiệu điện thế, tần số, v.v..).

###2. Internet layer( tầng internet)
####2.1 Chức năng:
- Có nhiệm vụ gửi các gói tin đến các mạng khác.
- Gửi dữ liệu từ nguồn tới đích bằng chế độ định tuyến.
- Định danh địa chỉ máy chủ và định danh.
- Định tuyến các gói tin.

###3. Transport layer( tầng giao vận)
####3.1 Chức năng:
- Đảm bảo độ tin cậy của gói tin.
- Đảm bảo tính thứ tự của dữ liệu.
- Sửa lỗi dữ liệu.
- Các gói tin bị lỗi được gửi lại.
- Giải quyết sự tắc nghẽn.

###4. Application( tầng ứng dụng)
####4.1 Chức năng:
- Là nơi các ứng dụng mạng liên kết với nhau giữa các nút.
- Trình bày, biểu diễn thông tin đến người dùng.
- Mã hóa, giải mã, điều khiển hội thoại.

####4.2 Các giao thức:
#####4.2.1 FTP (File Transfer Protocol):
- Là dịch vụ tạo cầu nối tin cậy.
- Sử dụng giao thức TCP để truyền các tập tin.
- Hỗ trợ truyền file nhị phân.

#####4.2.2 FTP (Trivial File Transfer Protocol):
- Khác với FTP là một dịch vụ không tạo cầu nối sử dụng giao thức UDP.
- DÙng trên router để truyền các file cấu hình.

#####4.2.3 SMTP (Simple Mail Transfer Protocol):
- SMTP quản lý hoạt động truyền e-mail qua mạng máy tính.

#####4.2.4 Telnet (Terminal emulation):
- Cung cấp khả năng truy cập từ xa vào một thiết bị đầu cuối khác. Cho phép người khác đăng nhập và thực thi các lệnh từ xa.

#####4.2.5 SNMP (Simple Network Management Protocol):
- Là một giao thức cung cấp một phương pháp để giám sát và điều khiển các thiết bị mạng và để quản lý các cấu hình, thu thập thống kê, hiệu suất và bảo mật.

#####4.2.6 DNS (Domain name system):
- Là một giao thức phân giải tên miền từ dạng số sang dạng chữ La-tinh.  
