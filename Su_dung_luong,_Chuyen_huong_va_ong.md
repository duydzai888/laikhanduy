# Sử dụng luồng, chuyển hướng và đường ống
### Chuyển hướng đầu vào, đầu ra
Khi các lệnh được thực thi, theo mặc định sẽ có 3 luồng:
1. Đầu vào tiêu chuẩn hoặc `stdin`
1. Đầu ra tiêu chuẩn hoặc `stdout`
1. Lỗi tiêu chuẩn hoặc `stderr`

Trong linux , tất cả các tệp đang mở được thể hiện bên trong bằng cái được gọi là bộ mô tả tệp . Nói một cách đơn giản, chúng được biểu thị bằng các số bắt đầu từ 0. Các `stdin` là tập tin mô tả 0, `stdout`là tập tin mô tả 1, `stderr` là tập tin mô tả 2.
#### Sử lí đầu ra tiêu chuẩn
Ghi đè đầu ra lệnh vào file (`passwd1`)
```
[root@laiduy ~]# grep -E "^root|^dbus" /etc/passwd
root:x:0:0:root:/root:/bin/bash
dbus:x:81:81:System message bus:/:/sbin/nologin
```
```
[root@laiduy ~]# grep -E "^root|^dbus" /etc/passwd > passwd1
```
```
[root@laiduy ~]# cat passwd1
root:x:0:0:root:/root:/bin/bash
dbus:x:81:81:System message bus:/:/sbin/nologin
```
Ghi nối tiếp đầu ra lệnh vào 1 tệp
```
[root@laiduy ~]# echo "Lai Khanh Duy dep trai" >> passwd1
```
```
[root@laiduy ~]# cat passwd1
root:x:0:0:root:/root:/bin/bash
dbus:x:81:81:System message bus:/:/sbin/nologin
Lai Khanh Duy dep trai
```
#### Quy định đầu vào tiêu chuẩn
Sử dụng đầu vào là file `khanhduy.txt`
```
[root@laiduy ~]# cat khanhduy.txt
Ho va ten: Lai Khanh Duy
```
```
[root@laiduy ~]# tr " " "," < khanhduy.txt
Ho,va,ten:,Lai,Khanh,Duy
```
### Dữ liệu đường ống giữa các chương trình
Chuyển hướng **STDOUT**, **STDIN**, **STDERR** giữa nhiều lệnh, trên 1 dòng lệnh. Sử dụng `|`để chuyển hướng đầu ra thành đầu vào của lệnh.Cú pháp: `Command1 | Command2 [| Command]...`-> đầu ra của `Command1` thành đầu vào của `Command2`
#### Sử dụng sed
Sử dụng `sed` commandđể chỉnh sửa file mà không cần mở file
- Thay `khanh` thành `ngoc`:
```
[root@laiduy ~]# echo "lai khanh duy" | sed 's/khanh/ngoc/'
lai ngoc duy
```
- Nếu có nhiều biến `khanh` thì ta phải sử dụng `g`để đặt thành global, lúc đó tất cả các biến mới được thay thế
```
[root@laiduy ~]# echo "lai khanh duy khong duoc sinh ra vao ngay quoc khanh" | sed 's/khanh/ngoc/'
lai ngoc duy khong duoc sinh ra vao ngay quoc khanh
```
```
[root@laiduy ~]# echo "lai khanh duy khong duoc sinh ra vao ngay quoc khanh" | sed 's/khanh/ngoc/g'
lai ngoc duy khong duoc sinh ra vao ngay quoc ngoc
```
- Sửa file 
```
[root@laiduy ~]# cat duy.txt
Gioi tinh: nam
Que quan: Tuyen Quang
```
```
[root@laiduy ~]# sed 's/nam/trai/' duy.txt
Gioi tinh: trai
Que quan: Tuyen Quang
```
- Xóa 1 từ trong file
```
[root@laiduy ~]# cat duy.txt
Gioi tinh: nam
Que quan: Tuyen Quang
[root@laiduy ~]# sed '/Quang/d' duy.txt
Gioi tinh: nam
```
#### Tạo dòng lệnh
Sử dụng `xargs` command để xây dựng và thực thi các lệnh từ đầu vào tiêu chuẩn.

