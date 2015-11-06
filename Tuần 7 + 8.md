#Một số câu lệnh đơn giản trong MySQL

##Đăng nhập:
Với quyền root:
>**mysql -u root -p**

Với 1 user nhất định:
>**mysql -u __tên user__ -p**
##Database:
Tạo một database có tên kma:
>**CREATE DATABASE kma;**

Sử dụng database đó:
>**USE kma;**

Liệt kê các database:
>**SHOW DATABASES;**
##User:
Tạo 1 user với tên phantom có password là 113phantom:
>**CREATE USER phantom@localhost IDENTIFIED BY '113phantom';**

Set quyền cho user đó với database kma:
>__GRANT ALL PRIVILEGES ON kma.*TO phantom@localhost;__

Xóa user
>**DROP USER "phantom'@'localhost";**

##Table:
###Tạo một bảng:
>**CREATE TABLE info;**

###Load data vào trong bảng đó:
Từ 1 file có sẵn:

Đầu tiên tạo 1 table có tên **info** với các cột:

![](https://cloud.githubusercontent.com/assets/14356333/10989628/529dc72e-847c-11e5-9acd-7e1224a1b2b0.jpg)

tạo 1 file info.txt đường dẫn /home/userver1.txt

![](https://cloud.githubusercontent.com/assets/14356333/10989518/d4e9d134-847a-11e5-976f-2cdf2e9121f4.jpg)

Mỗi dấu tab là sự ngăn cách giữa các cột, vị trí nào không có thông tin ta để **\N**. Sau đó load data của file info.txt vào bảng info trong MySQL. Sau đó dùng lệnh **SELECT * FROM info** để kiểm tra.

![](https://cloud.githubusercontent.com/assets/14356333/10989653/cb83dd9a-847c-11e5-84e7-f5247c22d137.jpg)

#Xây dựng trang web bằng wordpress:
https://www.youtube.com/watch?v=F05epVTn4wM&feature=youtu.be

