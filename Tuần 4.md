#Cài đặt phần mềm trên các distro khác nhau
##Ubuntu - debian
###1. Cài đặt các file định dạng deb:
Chúng ta hỉ cần click đúp vào file và trình cài đặt phần mềm trên hệ thống tự mở, click “Install Package” và chờ quá trình cài đặt hoàn tất.

Chú ý: một số phần mềm yêu cầu máy phải cài sẵn một số Dependency, nếu không đủ các Dependency lúc cài đặt sẽ báo lỗi. Để giải quyết vấn đề Dependency với file .deb nhanh gọn có thể sử dụng gói Gdebi
Đây là một ứng dụng có giao diện người dùng, nó cho phép chúng ta cài đặt các gói .deb đã dowload sẵn và nằm trên HDD, còn các Dependency phải kết nối Internet đề Gdebi tự tìm và download giúp chúng ta. Gdebi cũng có thể chạy trong chế độ non-GUI bằng cách chuyển tới folder chứa file .deb và gõ sudo gdebi package_name.deb tại nhắc lệnh và vẫn có khả năng giải quyết các dependency.

###2. Cài đặt các file định dạng rpm:
Sử dụng gói Alien để chuyển từ .rpm sang .deb cho dễ cài đặt

- Vào terminal, gõ sudo apt-get install alien để tải và cài đặt gói Alien thông qua tiện ích quản lý gói APT.

- Gõ vào Password ứng với User đang Logon. Gõ ‘y’ để đồng ý cài đặt gói Alien.

- Sau khi cài xong Alien, chúng ta chuyển file .rpm tới Desktop rồi mở Terminal, gõ cd + đường dẫn file.

- Bây giờ, gõ sudo alien -k filename.rpm để convert từ file .rpm sang .deb. Sau đó chúng ta cài file .deb như trên

###3. Cài đặt các file định dạng bin:
Tải và lưu file .bin tới lưu. Mở Terminal và gõ cd + đường dẫn file.

- Gõ tiếp sudo chmod +x filename.bin để cấp quyền thực thi file đó.

- Gõ ./filename.bin.

Sau đó chờ cho chương trình cài xong trong Terminal!

###4. Cài dặt phần mềm bằng Tarball:

Một tarball (thường là các file .tar , .tar.gz , .tgz , .tar.bz2 , .tbz2 ) gồm có mã nguồn cho chương trình mà chúng ta phải tự biên dịch, trình biên dịch (compile) như GCC… thì thường có sẵn trong Linux . Các bước cài đặt Tarball về cơ bản như sau

####4.1. Giải nén tarball:
Với những người còn mới với Linux thì tarball là một thuật ngữ được sử dụng chung nhằm ám chỉ một file có chứa các file khác. Nó gần giống như một file nén ZIP hoặc RAR trong Windows, ngoại trừ chương trình tar không nén các file

Tar làm việc với một chương trình nén như gzip để nén các file, đây là lý do tại sao chúng ta thấy hai đuôi mở rộng (.tar và .gz). Các đuôi mở rộng này đôi khi còn được viết tắt là .tgz

Tuy nhiên không cần phải chạy hai chương trình riêng biệt để bung các file mà chúng ta chỉ cần lệnh cho tar chạy các file thông qua gzip để giải nén. Chúng ta có thể sử dụng tiện ích đồ họa để bung các file này bằng cách kích đúp vào tarball từ bộ quản lý file của mình, hoặc có thể thực hiện điều đó bằng dòng lệnh:

$ tar zxvf file.tar.gz hoặc

$ tar zxf file.tar.gz

$ tar zxf file.tgz

$ tar jxf file.tar.bz2

$ tar jxf file.tbz2

Các tùy chọn chúng ta cung cấp cho tar được mô tả bên dưới:

 • -z để lệnh cho tar chạy file này thông qua gzip để giải nén (sử dụng –j cho các file bzip)

 • -x để bung các file

 • -v cho “verbose”, để chúng ta có thể thấy danh sách các file đang bung

 • -f để lệnh cho tar rằng chúng ta đang làm việc với một file

####4.2. Configure:
Khi các file được bung ra, mở một command terminal và vào thư mục nơi các file được giải nén trong đó. Trước khi biên dịch, chúng ta cần chạy kịch bản cấu hình. Công việc của kịch bản cấu hình là kiểm tra hệ thống của chúng ta về tất cả những gì phần mềm cần thiết để biên dịch chương trình từ mã nguồn thành chương trình nhị phân có thể sử dụng được. Nó sẽ tìm kiếm những thứ như phiên bản GCC và các công cụ cần thiết khác để xây dựng phần mềm. Khi chúng ta nằm trong thư mục với tất cả các file đã được bung từ tarball (sử dụng lệnh cd để change directory), hãy đánh vào ./configure

Nếu tất cả đều diễn ra tốt đẹp, lệnh trên sẽ kiểm tra một loạt các phần khác nhau của hệ thống chúng ta.

Vấn đề gây ra lỗi chung nhất trong bước này là mất dependency. Quan sát bất cứ lỗi nào mà chúng ta gặp phải để xác định xem gói phần mềm nào bị thiếu.

####4.3. Make
Đây là phần quan trọng nhất của quá trình biên dịch mã nguồn thành một chương trình có khả năng chạy. Đây là bước đơn giản nhất, chỉ yêu cầu một lệnh đơn giản. Nếu bước cấu hình hoàn tất mà không có lỗi, chúng ta chỉ cần đánh vào  make

Đối với các chương trình lớn, bước này có thể mất đến vài phút. Khi quá trình kết thúc, chúng ta sẽ được đưa quay trở lại shell nhắc lệnh

Chương trình của chúng ta lúc này đã hoàn toàn sẵn sàng cho sử dụng. Mặc dù vậy chúng ta vẫn nên chạy thêm một bước nữa để chương trình có thể được cài đặt hoàn toàn vào đúng location và có thể chạy từ bất cứ đâu.

####4.4. Make install:

Tất cả những gì cần thiết lúc này là copy chương trình vừa được biên dịch vào các thư mục hệ thống như /usr/bin để có thể chạy từ bất cứ thư mục nào mà không cần chỉ định đường dẫn đến các file. Do nó sẽ copy đến một thư mục bên ngoài thư mục chủ nên chúng ta có thể cần đến các đặc quyền root. Nếu bước này được hoàn tất mà không có lỗi, chúng ta hãy chạy sudo make install để copy các file. Đến đây, chúng ta đã hoàn thành xong phần việc của mình. Chương trình mới của chúng ta có thể được sử dụng giống như bất cứ chương trình nào đang chạy khác.

Cài đặt phần mềm trên Redhat – Centos

Bản thân các gói RPM không chứa chương trình cài đặt, nó chỉ chứa các thông tin về các file sẽ được cài đặt, thông tin mô tả về phần mềm chứa trong gói và các file nằm trong gói RPM sẽ được cài đặt vào thư mục nào trong hệ thống. Các gói phần mềm dạng RPM được cài đặt vào hệ thống nhờ vào chương trình RPM có trong hệ thống.

Cách đơn giản nhất để cài một gói RPM, chẳng hạn gói foobar-1.0-1.i386.rpm là dùng lệnh:

rpm -i foobar-1.0-1.i386.rpm

Để theo dõi quá trình install, chúng ta có thể thêm tham số:

rpm –ivh foobar-1.0-1.i386.rpm

Để uninstall package đã được cài:

rpm -e foobar

Nếu có một file RPM mà không biết nó là phần mềm nào, chúng ta có thể lấy thông tin bằng lệnh:

rpm -qpi koules-1.4-1.i386.rpm

Nếu đã lỡ xóa một vài file nào đó và không chắc chắn rằng file đó đang còn cần thiết cho chương trình nào đó, chúng ta có thể xem thử hệ thống đang thiếu file cần thiết nào:

rpm –Va

Thường khi cài một gói RPM nào đó, đòi hỏi phải cài thêm các gói phụ thuộc, chúng ta phải đi tìm và cài đặt các gói phụ thuộc trước khi cài được gói phần mềm trên. Hoặc cũng có thể gộp chung lại trên một dòng lệnh với lệnh RPM một danh sách các file RPM, được cách nhau bởi dấu khoảng trắng.

Trong Redhat hoặc Mandrake ở các phiên bản mới, Software Package Installation cũng tương tự như trình Add/Removed Software trong Windows vậy. Các tiện ích đi kèm trong bộ cài đặt được liệt kê đầy đủ theo từng nhóm để tiện theo dõi. Khi cài đặt một phần mềm, chương trình sẽ tự động kiểm tra các gói phụ thuộc và sẽ yêu cầu chúng ta đưa các CD cần thiết vào trong quá trình cài đặt.

Một kiểu cài đặt phần mềm phổ biến khác là chúng ta cài đặt từ các gói mã nguồn, thường được viết bằng ngôn ngữ C. Các gói này có dạng file nén *.TAR.GZ, *.BZ hoặc *.SRC.RPM. Trong trường hợp này, máy tính của chúng ta phải có sẵn các bộ công cụ biên dịch và các thư viện lập trình.

Sở dĩ phải có dạng TAR vì các file phải được gói lại thành một file trước khi nén thành GZ hoặc BZ, chứ không thể nén trực tiếp từ nhiều file thành một file nén được. Bản thân file *.TAR không phải là một file nén mà chỉ là một file chứa một tập các file khác gom lại mà thôi.

Với các gói nén bằng TAR.GZ, chúng ta bung nén như sau:

tar xvzf file.tar.gz

Sau khi giải nén, một thư mục chứa các file trong file nén được tạo ra. chúng ta vào thư mục này và thực hiện quá trình biên dịch theo như file INSTALL hướng dẫn. Các bước thông thường (chứ không phải tất cả) là như sau:

./configure

make

make install

Bước chạy lệnh configure là để chương trình script xác lập cấu hình hệ thống cho việc biên dịch chương trình. Tùy vào cấu hình máy mà có chế độ biên dịch phù hợp và tối ưu cho chính hệ thống đó.

Lệnh make dùng để biên dịch mã nguồn thành file thực thi. Sau đó lệnh install để cài đặt file đã biên dịch lên hệ thống.

chúng ta cũng có thể dùng lệnh yum để cài đặt phần mềm, vd chúng ta muốn cái webserver gõ lệnh sau

 yum install httpd

Sau đó nhấn -y để xác nhận, hoặc có thể tìm một gói cài đặt bằng cách dùng lệnh yum search, sẽ liệt kê các gói cần cài đặt

 yum search httpd

#Sự khác nhau giữa update, upgrade, dist-upgrade
##1. Update:
Cập nhật danh sách các gói cài đặt và phiên bản sẵn có nhưng không cài đặt hoặc nâng cấp bất kì các gói cài đặt nào.

##2. Upgrade:
Cài đặt phiên bản mới hơn của gói cài đặt đang có( sau khi đã cập nhật các gói cài đặt). Vậy chúng ta cần cập nhật các gói cài đặt trước khi nâng cấp phiên bản mới. Upgrade sẽ **không xóa đi** các gói cài đặt cũ.


##3. Upgrade:
Cũng giống như upgrade nhưng dist-upgrade cung cấp thêm hệ thống sửa lỗi xung đột giữa các gói cài đặt. Có nghĩa là nếu như chúng ta dùng upgrade thì sẽ có khả năng các gói cài đặt bị xung độ, lúc đó ta sẽ sử dụng dist-upgrade để xử lí các gói cài đặt nếu bị xung đột( thay thế gói cài đặt cũ bằng cách xóa đi nó và cài gói mới hơn).

#Thiết lập 2 card mạng trong ubuntu:
Để thiết lập card mạng trong ubuntu server ta truy cập vào tập tin interfaces nằm trong đường dẫn /etc/network sau đó nhập mật khẩu
![](https://cloud.githubusercontent.com/assets/14356333/10410265/48992d84-6f66-11e5-9c98-8fefea709307.jpg)

Tiếp theo, cấu hình cho 2 card mạng eth0 và eth1 cùng một dải ip 192.168.1.0 ta gõ vào các thông số tương ứng address, network, netmask, broadcast, gateway.
Nếu dùng dhcp thì thay static bằng dhcp và xóa các thông số bên dưới.
![](https://cloud.githubusercontent.com/assets/14356333/10410280/2009b55e-6f67-11e5-9c2a-5f58140f10e1.jpg)

Sau khởi động lại mạng 
![](https://cloud.githubusercontent.com/assets/14356333/10410299/0e1fc422-6f68-11e5-8da2-250ca4ec2990.jpg)



