
# Xử lí văn bản bằng bộ lọc
### Các lệnh kết hợp tệp
Sử dụng lệnh `cat` để xem nội dung các file
```
[root@laiduy ~]# cat khanhduy.txt
Ho va ten: Lai Khanh Duy
Nam sinh: 2002
```
```
[root@laiduy ~]# cat duy.txt
Gioi tinh: nam
Que quan: Tuyen Quang
```
Sử dụng lệnh `paste` để ghép nội dung file theo kiểu `site to site`
```
[root@laiduy ~]# paste khanhduy.txt duy.txt
Ho va ten: Lai Khanh Duy        Gioi tinh: nam
Nam sinh: 2002  Que quan: Tuyen Quang
```
### Lệnh chuyển đổi tệp
Sử dụng lệnh `od` để chuyển file sang dạng `octal`
```
[root@laiduy ~]#od khanhduy.txt
0000000 067510 073040 020141 062564 035156 046040 064541 045440
0000020 060550 064156 042040 074565 047012 066541 071440 067151
0000040 035150 031040 030060 000062
0000047
```
### Lệnh định dạng tệp
Sử dụng lệnh `sort` để sắp xếp đầu ra các file theo thứ tự
```
[root@laiduy ~]#sort khanhduy.txt
Ho va ten: Lai Khanh Duy
Nam sinh: 2002
```
- [ ] Tùy chọn `-n` để sắp xếp theo thứ tự ngược lại
### Đánh số bằng lệnh `nl`
SỬ dụng lệnh `nl` để đánh số các dòng trong file 
```
[root@laiduy ~]#nl khanhduy.txt
     1 Ho va ten: Lai Khanh Duy
     2 Nam sinh: 2002
```
### Lệnh xem tệp
#### Dùng `more` hoặc `less`
Lệnh `more` và `less` được sử dụng để xem file dưới dạng cuộn
#### Nhìn vào file với phần `head`
```
[root@laiduy ~]#head /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
```
Tùy chọn `-n` được dùng để xem số dòng đầu theo ý muốn
```
[root@laiduy ~]# head -n3 /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
```
### Xem tệp với `tail`
Ngược lại với lệnh `head`, lệnh `tail`được dùng để xem số dòng cuối cùng của file, mặc định là 10.
```
[root@laiduy ~]# tail /etc/passwd
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
laikhanhduy:x:1000:1000:laikhanhduy:/home/laikhanhduy:/bin/bash
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
nginx:x:998:996:nginx user:/var/cache/nginx:/sbin/nologin
khanhduy:x:1001:1001::/home/khanhduy:/bin/bash
duykhanh:x:1002:1002::/home/duykhanh:/bin/bash
```
Tùy chọn `-n`được sử dụng để hiển thị số dòng , số từ, số byte của 1 file cụ thể.
```
[root@laiduy ~]# tail -n5 /etc/passwd
laikhanhduy:x:1000:1000:laikhanhduy:/home/laikhanhduy:/bin/bash
apache:x:48:48:Apache:/usr/share/httpd:/sbin/nologin
nginx:x:998:996:nginx user:/var/cache/nginx:/sbin/nologin
khanhduy:x:1001:1001::/home/khanhduy:/bin/bash
duykhanh:x:1002:1002::/home/duykhanh:/bin/bash
```
### Các lệnh tóm tắt tệp
#### Đếm với lệnh `wc`
`wc` command được sử dụng để hiển thị số dòng, số từ , số byte của 1 file cụ thể.
```
[root@laiduy ~]# wc duy.txt
 1  7 36 duy.txt
```
#### Kéo các phần ra với `cut`
Sử dụng lênh `cut` để cắt 1 số kí tự hoặc text để file hiển thị theo ý nuốn.
```
[root@laiduy ~]# head -n2 /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
```
```
[root@laiduy ~]# head -n2 /etc/passwd | cut -d ":" -f 1,7
root:/bin/bash
bin:/sbin/nologin
```
#### Khám phá các dòng lặp lại với `uniq`
Sử dụng `uniq` để loại bỏ các dòng trùng lặp trong file 
```
[root@laiduy ~]# cat bai1.txt
Lai Khanh Duy
Lai Khanh Duy

2002
2002

Tuyen Quang
Tuyen Quang
```
```
[root@laiduy ~]# uniq bai1.txt
Lai Khanh Duy

2002

Tuyen Quang
```
#### Phân tích 1 thuật toán MD5
Kiểm tra tính toàn vẹn của file sử dụng hàm băm MD5
```
[root@laiduy ~]# md5sum duy.txt
83d336ac199a850181c867ff8480d6fb  duy.txt
```
#### Bảo mật thuật toán băm
Thuật toán hàm băm an toàn cũng được sử dụng để  xác minh tính toàn vẹn của file nó được sao chép hoặc di chuyển sang 1 vị trí khác





