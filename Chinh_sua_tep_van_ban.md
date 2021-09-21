# Chỉnh sửa tệp văn bản
### Nhìn vào trình chỉnh sửa văn bản
Một số trình soạn thảo trên Linux: Vi, Vim nano, geany, ...
### Tìm hiểu về trình soạn thảo Vim
Trình soạn thảo `Vim` có 3 chế độ:
- Chế độ `Command mode` là chế độ bình thường, tại đây ta sẽ nhập các tổ hợp phím để thực hiện lệnh.
- Chế độ `Insert` là chế độ chỉnh sửa , nhập.
- Chế độ `Esc`, các lệnh nhập ở đây được để sau dấu " : ".
### Khám phá các thủ tục soạn thảo văn bản cơ bản
Di chuyển: 
```
h: Di chuyển con trỏ chuột sang trái
j: Di chuyển con trỏ chuột xuống dưới
k: Di chuyển con trỏ chuột lên trên
l: Di chuyển con trỏ chuột sang phải
$: Di chuyển con trỏ chuột xuống cuối dòng
0: Di chuyển con trỏ chuột về đầu dòng 
gg: Di chuyển con trỏ chuột về đầu văn bản
G: Di chuyển con trỏ chuột xuống cuối văn bản
Ctrl y: Cuộn lên văn bản 1 dòng
Ctrl e: Cuộn xuống văn bản 1 dòng
Ctrl u: Cuộn lên văn bản nửa màn hình
Ctrl d: Cuộn xuống văn bản nửa màn hình
```

Thay đổi chế độ:
```
i: Chuyển sang chế độ Insert
v: Chuyển sang chế độ Visual
V: Chuyển sang chế độ Visual Line ( chọn hàng thay vì chọn từ như Visual )
ESC: Chuyển sang chế độ Normal
```

Thao tác với văn bản:
```
x: Xóa kí tự tại con trỏ
y: Copy phần văn bản đã chọn trong chế độ Visual
p: Paste phần văn bản đã lưu
d: Delete văn bản
d2w: Xóa 2 lần từ đằng sau con trỏ ( delete ... word )
d$: Xóa đến cuối dòng
d3b: Xóa 2 từ đằng trước con trỏ ( delete ... backwards )
dt): Xóa đến kí tự  " ) " ( delete till ... )
d2j: Xóa 2 dòng từ dưới lên 
d2h: Xóa 2 chữ bên trái
dd: Xóa dòng hiện tại của con trỏ
u: Undo
Ctrl r: Redo
```

### Lưu thay đổi
Các lệnh dùng để lưu:
```
:w: Lưu văn bản
:wq: Lưu và thoát văn bản
:q!: Thoát và không lưu
```

