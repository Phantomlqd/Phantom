#Mô hình OSI
##I. Khái niệm:
- OSI là viết tắt của Open Systems Interconnection model- mô hình liên kết các hệ thống mở, còn được gọi là mô hình 7 tầng OSI. 
- Là mô hình khái niệm về sự định tính và chuẩn hóa các chức năng giao tiếp của một hệ thống viễn thông hoặc một hệ thống máy tính mà không cần quan tâm tâm đến cấu trúc bên trong và công nghệ.
- Nhiệm vụ của nó là đảm bảo khả năng tương tác và liên kết của các hệ thống truyền thông nó cấu trúc khác nhau bằng các giao thức tiêu chuẩn.
- Được xây dựng dựa trên cấu trúc phân tầng với 7 tầng liên kết với nhau có chức năng và nhiệm vụ khác nhau.

##II. Các tầng trong mô hình OSS
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
