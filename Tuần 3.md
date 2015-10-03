#Tạo, sửa, xóa user và group
##Tạo user:
###Tạo một tài khoản người dùng mới
Để tạo một tài khoản người dùng mới vào hệ thống, chúng ta sử dụng câu lệnh useradd. 

Cú pháp :
useradd [options] <tên người dùng> 

Lệnh useradd sẽ tự động tạo các file của người dùng trên hệ thống, tạo thư mục home của người dùng và một số thông tin cấu hình khác phụ thuộc vào các option sử dụng. Khi một tài khoản người dùng mới được tạo ra, một tài khoản nhóm người dùng cùng tên với người dùng cũng sẽ tự động được tạo ra trên hệ thống. 

###Một số option với lệnh useradd :
-d /home_directory : Tạo thư mục home cho người dùng. Chúng ta thường tạo thư mục home trùng với tên của người dùng và thường đặt là thư mục /home/[tên người dùng].

-e date : Xác định ngày mà tài khoản người dùng sẽ bị vô hiệu hóa trên hệ thống. Định dạng của ngày được đặt như sau YYYY-MM-DD (Năm-Tháng-Ngày).

-g group : Xác định tài khoản người dùng thuộc nhóm người dùng nào trên hệ thống. 

-G groups : Xác định tài khoản người dùng thuộc những nhóm người dùng nào trên hệ thống (một người dùng có thể thuộc nhiều nhóm khác nhau).

-s shell : Xác định shell mặc định của người dùng khi đặng nhập vào hệ thống. 

-u uid : Xác định số user id của người dùng. 

##Sửa user:
###Tạo mật khẩu và thay đổi mật khẩu của người dùng
Để tạo mật khẩu hoặc thay đổi mật khẩu cho người dùng chúng ta sử dụng lệnh passwd.
Cú pháp : passwd [tên người dùng]
 
###Xóa một tài khoản người dùng:
Để xõa một tài khoản người dùng chúng ta sử dụng câu lệnh :

userdel [options] [tên người dùng]

Lệnh này sẽ xóa tài khoản người dùng trong 2 file /etc/passwd và /etc/shadow. Người dùng không thể đăng nhập vào hệ thống khi tài khoản của người dùng đã bị xóa. Chúng ta sử dụng thêm option -r để xóa thư mục home của người dùng và các file có trong thư mục home. 

Ví dụ : Để xóa tài khoản người dùng ipmac và thư mục home của người dùng ipmac trên hệ thống, chúng ta sử dụng câu lệnh sau : 

###Chỉnh sửa một tài khoản người dùng:
Để chỉnh sửa một số thông tin của tài khoản người dùng chúng ta sử dụng câu lệnh usermod. Câu lệnh usermod cho phép chúng ta chỉnh sửa một tài khoản người dùng với các tiêu chí sau : thay đổi thư mục home của người dùng, thay đổi thời gian hết hạn của tài khoản, thay đổi nhóm của người dùng, thay đổi tên đăng nhập, thay đổi login shell … 

**Các option dùng với usermod giống với các option sử dụng với lệnh useradd** 

Cú pháp: usermod [options] [tên người dùng]

##Tạo group:
###Tạo một nhóm người dùng mới
Để tạo một nhóm người dùng mới chúng ta sử dụng câu lệnh groupadd với các option tùy chọn.

Cú pháp : groupadd [options] [tên người dùng]

###Các option : 
-g gid : Đặt số group id cho nhóm người dùng. 

-f : Bắt câu lệnh chạy mà không thông báo lỗi nếu đã có một nhóm trên hệ thống trùng với tên nhóm định tạo.
Và một số option khác. 

Ví dụ : Tạo một nhóm có tên phantom với số group id của nhóm là 123 

groupadd -g 123 phantom

##Sửa group:
###Xóa một nhóm người dùng
Để xóa một nhóm chúng ta sử dụng câu lệnh groupdel. Chức năng của lệnh groupdel giống với lệnh userdel sẽ xóa toàn bộ thông tin của nhóm khỏi hệ thống (thông tin trong file /etc/group). Trước khi xóa một nhóm khỏi hệ thống chúng ta cần đảm bảo rằng không có người dùng nào đang yêu cầu truy cập đến nhóm đó. 

Cú pháp : groupdel [tên nhóm]

###Chỉnh sửa một nhóm người dùng
Để chỉnh sửa một nhóm chúng ta sử dụng câu lệnh groupmod. Chức năng của lệnh groupmod giống chức năng của lệnh usermod. 
Cú pháp : groupmod [options] [tên nhóm]

#Các câu lệnh sửa xóa file, folder
- ls: liệt kê tất cả các tập tin có thể nhìn thấy trong thư mục hiện hành.
- mkdir: Tạo thư mục mới.
- cp/mv: Sao chép hoặc di chuyển tệp tin từ nơi này đến nơi khác.
- rm: Xóa tệp tin hoặc thư mục.
- vi/nano: Chỉnh sửa hoặc xem tập tin.
- chmod: Thay đổi quyền thao tác tập tin.
u: người đang dùng                      
r: đọc
g: nhóm                                              
w: viết
o: người dùng khác                       
x: thực thi
a: cho tất cả người dùng
- locate: Kiểm tra cơ sở dự liệu trong thư mục hiện hành.
- locate ABC
tìm kiếm và xem tất cả các đường dẫn và tập tin có tên bao gồm cụm từ đại diện “ABC”.
- touch : tạo file

#Phân tich gói tin TCP:
##Giới thiệu: 
Giao thức TCP (Transmission Control Protocol - "Giao thức điều khiển truyền vận") là một giao thức quan trọng trong bộ giao thức TCP/IP. Giúp các ứng dụng trên các máy chủ tạo ra kết nối với nhau. Giao thức này đảm bảo việc truyền dữ liệu tới nơi nhận một cách **tin cậy** và **đúng thứ tự**.
## Hoạt động của giao thức:
- Hoạt động của giao thức TCP có 3 bước: 
  - Thiết lập kết nối
  - Truyền dữ liệu
  - Kết thúc kết nối

###Thiết lập kết nối:
Để thiết lập một kết nối, TCP sử dụng một quy trình bắt tay 3 bước (3-way handshake) Trước khi client thử kết nối với một server, server phải đăng ký một cổng và mở cổng đó cho các kết nối: đây được gọi là mở bị động. Một khi mở bị động đã được thiết lập thì một client có thể bắt đầu mở chủ động. Để thiết lập một kết nối, quy trình bắt tay 3 bước xảy ra như sau:

Client yêu cầu mở cổng dịch vụ bằng cách gửi gói tin SYN (gói tin TCP) tới server, trong gói tin này, tham số sequence number được gán cho một giá trị ngẫu nhiên X.
Server hồi đáp bằng cách gửi lại phía client bản tin SYN-ACK, trong gói tin này, tham số acknowledgment number được gán giá trị bằng X + 1, tham số sequence number được gán ngẫu nhiên một giá trị Y
Để hoàn tất quá trình bắt tay ba bước, client tiếp tục gửi tới server bản tin ACK, trong bản tin này, tham số sequence number được gán cho giá trị bằng X + 1 còn tham số acknowledgment number được gán giá trị bằng Y + 1
Tại thời điểm này, cả client và server đều được xác nhận rằng, một kết nối đã được thiết lập.

###Truyền dữ liệu
Một số đặc điểm cơ bản của TCP để phân biệt với UDP:

Truyền dữ liệu không lỗi (do có cơ chế sửa lỗi/truyền lại)
Truyền các gói dữ liệu theo đúng thứ tự
Truyền lại các gói dữ liệu mất trên đường truyền
Loại bỏ các gói dữ liệu trùng lặp
Cơ chế hạn chế tắc nghẽn đường truyền
Ở hai bước đầu tiên trong ba bước bắt tay, hai máy tính trao đổi một số thứ tự gói ban đầu (Initial Sequence Number -ISN). Số này có thể chọn một cách ngẫu nhiên. Số thứ tự này được dùng để đánh dấu các khối dữ liệu gửi từ mỗi máy tính. Sau mỗi byte được truyền đi, số này lại được tăng lên. Nhờ vậy ta có thể sắp xếp lại chúng khi tới máy tính kia bất kể các gói tới nơi theo thứ tự thế nào.

Trên lý thuyết, mỗi byte gửi đi đều có một số thứ tự và khi nhận được thì máy tính nhận gửi lại tin báo nhận (ACK). Trong thực tế thì chỉ có byte dữ liệu đầu tiên được gán số thứ tự trong trường số thứ tự của gói tin và bên nhận sẽ gửi tin báo nhận bằng cách gửi số thứ tự của byte đang chờ.

###Kết thúc kết nối
Để kết thúc kết nối hai bên sử dụng quá trình bắt tay 4 bước và chiều của kết nối kết thúc độc lập với nhau. Khi một bên muốn kết thúc, nó gửi đi một gói tin FIN và bên kia gửi lại tin báo nhận ACK. Vì vậy, một quá trình kết thúc tiêu biểu sẽ có 2 cặp gói tin trao đổi.

Một kết nối có thể tồn tại ở dạng "nửa mở": một bên đã kết thúc gửi dữ liệu nên chỉ nhận thông tin, bên kia vẫn tiếp tục gửi.
