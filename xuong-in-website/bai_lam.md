# BÀI LÀM – HACKATHON 02

- **Mã đề:** 06
- **Họ tên:NGUYỄN TRUNG THÀNH**
- **Lớp:HNKS26CNTT3**
- **Link repository:**https://github.com/chup62/HN-KS26-CNTT3_Nhap-mon-CNTT_HACKATHON02
- **Hệ điều hành (Windows/macOS):Windows**

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
pwd
ls -Force
mv .\yeu_cau_khach_hang.txt .\docs
mkdir backup
cp .\data\don_in_thang_6.xlsx .\backup\
rm .\temp_606.tmp
cd logs
ls
cd ..
Get-ChildItem -Recurse -Force
```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
 Directory: C:\LamBaiTap\starter-kit\xuong-in-website


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        11/11/2026  10:47 AM                backup
d-----        11/11/2026  10:45 AM                data
d-----        11/11/2026  10:46 AM                docs
d-----        11/11/2026  10:44 AM                evidence
d-----        11/11/2026  10:45 AM                logs
d-----         11/3/2026   7:07 AM                web
-a----         11/3/2026   7:07 AM             76 .env
-a----         11/3/2026   7:07 AM           2407 bai_lam.md


    Directory: C:\LamBaiTap\starter-kit\xuong-in-website\backup


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           6137 don_in_thang_6.xlsx


    Directory: C:\LamBaiTap\starter-kit\xuong-in-website\data


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           6137 don_in_thang_6.xlsx


    Directory: C:\LamBaiTap\starter-kit\xuong-in-website\docs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM            153 yeu_cau_khach_hang.txt


    Directory: C:\LamBaiTap\starter-kit\xuong-in-website\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM            981 oder.log


    Directory: C:\LamBaiTap\starter-kit\xuong-in-website\web


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----         11/3/2026   7:07 AM                images
-a----         11/3/2026   7:07 AM            594 app.js
-a----         11/3/2026   7:07 AM            516 index.html
-a----         11/3/2026   7:07 AM            460 style.css


    Directory: C:\LamBaiTap\starter-kit\xuong-in-website\web\images


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         11/3/2026   7:07 AM           3092 logo-printnow.png

```

## 4.3. Lọc log truy cập website

### a) Lệnh lọc các dòng status=500

```shell
Get-Content .\logs\order.log | Select-String "status=500" >.\logs\loi_500.text
Get-Content .\logs\loi_500.text -Head 2
```

### 2 dòng đầu tiên trong logs/loi_500.txt

```text
2026-06-28 08:15:01 POST /api/thanh-toan status=500
2026-06-28 08:34:07 POST /api/tai-file status=500
```

### b) Lệnh đếm số dòng status=404 và kết quả

```shell
(Get-Content .\logs\order.log | Select-String "status=404").Count
```

```text
4
```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
.\tong_hop.ps1
```

### Nội dung file logs/tong_hop.txt

```text
=== BAO CAO SU CO WEBSITE ===

2026-06-28 08:08:39 GET /mau-tet-cu status=404
2026-06-28 08:19:12 GET /images/poster-2.jpg status=404
2026-06-28 08:23:23 GET /images/poster-2.jpg status=404
2026-06-28 08:54:24 GET /tin-tuc status=404




Count    : 6
Average  : 
Sum      : 
Maximum  : 
Minimum  : 
Property : 

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] README.md: Heading 1, mô tả có **in đậm** và *in nghiêng*, bảng, code block, task list, blockquote
- [x] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [x] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | --- | --- | --- |
| 1 | Network | Tên file logo bị sai tên không hiển thị được | Vào file html để sửa lại tên đúng |
| 2 | Console | app.js:18 Uncaught ReferenceError: hienThiSanPham is not defined | Vào file .js sửa lại dòng 18 cho đúng tên đã dùng |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- **Context: Tôi là sinh viên năm nhất chưa bao giờ fix lỗi hiển thị** 
- **Expected: Bây giờ trang web xưởng in ấn của tôi muốn có đủ dữ liệu ở bảng hiển thị giao diện** 
- **Actual: Dữ liệu trên trang web không có gì và tôi vào tab console thấy thông báo lỗi app.js:18 Uncaught ReferenceError: hienThiSanPham is not defined** 
- **Log: app.js:18 Uncaught ReferenceError: hienThiSanPham is not defined** 
 
### Câu tìm kiếm Google

```text
site:stackoverflow.com "Uncaught ReferenceError"
```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/don_in_thang_6.xlsx`, không cần ghi vào đây.
