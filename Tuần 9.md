#1. Viết script cài đặt wordpress trên ubuntu server:
    #!/bin/bash
    cd /home/userver2
    sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password password 113phantom'
    sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password_again password 113phantom'
    sudo apt-get -y install mysql-server mysql-client
    sudo apt-get -y install php5 libapache2-mod-php5
    sudo apt-get -y install php5-mysql php5-curl php5-gd php5-intl php-pear php5-imagick php5-imap php5-mcrypt php5-memcache     php5-ming php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
    sudo mysql -u root -p113phantom << EOF
    CREATE DATABASE wordpress;
    CREATE USER phantom13@localhost IDENTIFIED BY '113phantom';
    GRANT ALL PRIVILEGES ON wordpress.* TO phantom13@localhost;
    FLUSH PRIVILEGES;
    exit
    EOF
    cd /var/www
    sudo wget wordpress.org/latest.tar.gz
    sudo tar xzvf latest.tar.gz
    cd wordpress
    sudo cp wp-config-sample.php wp-config.php
    sed -i 's/database_name_here/'wordpress'/g' /var/www/wordpress/wp-config.php
    sed -i 's/password_here/'113phantom'/g' /var/www/wordpress/wp-config.php
    sed -i 's/username_here/'phantom13'/g' /var/www/wordpress/wp-config.php
    sudo chown -R www-data:www-data /var/www/wordpress
    sudo mkdir /var/www/wordpress/wp-content/uploads -p
    sudo chown -R :www-data /var/www/wordpress/wp-content/uploads
    sudo service apache2 restart

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
