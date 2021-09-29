# Sử dụng biểu thức chính quy
### Sử dụng grep
Sử dụng lệnh `grep` để đọc văn bản, nó rất mạnh trong việc sử dụng `reguler expression`.
Cú pháp: `grep [Option] Pattern [File...]`
```
[root@laiduy ~]# grep khanhduy.txt
Lai Khanh Duy 2002
```
### Hiểu các cụm từ thông dụng cơ bản 
Sử dụng grep để đếm số địa chỉ ip có trong file
```
[root@laiduy ~]# cat /var/log/secure | grep -Ec "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b"
1259
```
### Hiểu các cụm từ thông dụng mở rộng
Tìm từ `processor` trong file `/proc/cpuinfo`
```
[root@laiduy ~]# grep -E "^processor" /proc/cpuinfo
processor       : 0
processor       : 1
```