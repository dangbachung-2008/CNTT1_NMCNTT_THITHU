BÀI LÀM – THI THỬ HACKATHON 01

- **Mã đề:** Thi thử
- **Họ tên:** đặng bá chung 
- **Lớp:**cntt1  
- **Link repository:** 
- **Hệ điều hành (Windows/macOS):** windown

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shel
#1 hiển thị đường dẫn tuyệt đối
windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\Users\ADMIN\Downloads\starter-kit\Van Phong Pham Website FINAL> pwd

Path
----
C:\Users\ADMIN\Downloads\starter-kit\Van Phong Pham Website FINAL

#2 liệt kê các nội dung kể cả file ẩn 
PS C:\Users\ADMIN\Downloads\starter-kit\Van Phong Pham Website FINAL> ls -Force

    Directory: C:\Users\ADMIN\Downloads\starter-kit\Van Phong Pham Website FINAL

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        23/10/2026  10:51 AM             78 .env
-a----        23/10/2026  10:51 AM           6105 Don Ban Thang 10.xlsx
-a----        23/10/2026  10:52 AM           6053 Logo Van Phong Pham.PNG
-a----        23/10/2026  10:52 AM             51 Nhap Hang.txt
-a----        23/10/2026  10:52 AM           1053 Shop.log
-a----        23/10/2026  10:52 AM             22 temp_131.tmp
# 3. Di chuyển nhap_hang.txt vào docs và logo vào media
mv nhap_hang.txt docs/
mv logo_van_phong_pham.png media/
# 4. Sao chép logo từ media vào backup
cp media/logo_van_phong_pham.png backup/
# 5. Xoá file .tmp tại thư mục gốc
rm temp_131.tmp
# 6. Dùng đường dẫn tương đối vào logs, liệt kê nội dung rồi quay lại thư mục gốc
cd logs
ls -Force
cd ..

```

### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----       10/23/2026  10:00 AM                backup
d-----       10/23/2026  10:00 AM                data
d-----       10/23/2026  10:00 AM                docs
d-----       10/23/2026  10:00 AM                logs
d-----       10/23/2026  10:00 AM                media
-a-h--       10/23/2026  09:00 AM            128 .env
-a----       10/23/2026  10:00 AM           1520 auto_report.ps1
-a----       10/23/2026  10:00 AM           2048 bai_lam.md
-a----       10/23/2026  10:00 AM           1024 README.md

```

## 4.3. Lọc log thủ công

### Lệnh đã chạy

```shell
Get-Content logs/shop.log | Select-String "ERROR" > logs/daily_report.txt
Get-Content logs/daily_report.txt

```

### 2 dòng lỗi đầu tiên trong daily_report.txt

```text
[2026-10-20 08:15:22] ERROR: Database connection failed.
[2026-10-20 09:30:11] ERROR: Payment gateway timeout.

```

## 4.4. Thao tác với tài liệu Markdown (README.md)

> README.md được chấm trực tiếp trên file `README.md` ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [x] Heading 1: tên dự án
- [x] Mô tả ngắn có cả **in đậm** và *in nghiêng*
- [x] Bảng `Thư mục | Nội dung`, ít nhất 3 dòng dữ liệu
- [x]Code block chứa lệnh PowerShell/Terminal liệt kê nội dung dự án
- [x] Task list ít nhất 2 công việc, có ít nhất 1 mục đã hoàn thành
- [x] Blockquote nhắc không upload `.env`

## 4.5. Chạy script auto_report (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
Windows (PowerShell): .\auto_report.ps1

```

### Nội dung file logs/auto_report.txt

```text
=== BAO CAO LOI ===
[2026-10-20 08:15:22] ERROR: Database connection failed.
[2026-10-20 09:30:11] ERROR: Payment gateway timeout.
[2026-10-20 14:05:44] ERROR: Failed to write session data.

```

## 4.6. Đếm số dòng lỗi

### Lệnh

```shell
Get-Content logs/shop.log | Select-String "ERROR" | Measure-Object

```

### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)

```text 
Count    : 0
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

```

## 4.7. Báo cáo tổng hợp

### Các lệnh đã chạy

```shell
"=== TONG HOP LOG ===" > logs/tong_hop.txt
Get-Content logs/shop.log | Select-String "WARNING" >> logs/tong_hop.txt
(Get-Content logs/shop.log | Select-String "ERROR").Count >> logs/tong_hop.txt

```

### Nội dung file logs/tong_hop.txt

```text
=== TONG HOP LOG ===
[2026-10-20 08:00:10] WARNING: Memory usage exceeds 80%.
[2026-10-20 11:20:05] WARNING: Disk space running low.
3
```

## 4.8. Excel

> Phần Excel được chấm trực tiếp trên file `data/don_ban_thang_10.xlsx`, không cần ghi vào đây.

.


