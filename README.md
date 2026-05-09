# Log Archive

Bash script nén và lưu trữ thư mục log thành file `.tar.gz` có timestamp — hỗ trợ chạy thủ công hoặc lên lịch tự động mỗi đêm qua cron.

## Tính năng

| Mục | Mô tả |
|-----|-------|
| Archive thủ công | Nén ngay thư mục log chỉ định thành `.tar.gz` |
| Đặt lịch tự động | Cài cron job chạy lúc nửa đêm mỗi ngày |
| Hủy lịch | Gỡ cron job đã cài |
| Ghi log hoạt động | Mỗi lần archive được ghi vào `~/log-archives/archive.log` |

## Yêu cầu

- Bash >= 4
- `tar`, `date`, `crontab` — có sẵn trên mọi hệ thống Unix/Linux/macOS

## Cài đặt

```bash
git clone https://github.com/mid-guy/log-archive.git
cd log-archive
chmod +x log-archive
```

## Sử dụng

```bash
# Archive ngay lập tức
./log-archive <thư-mục-log>

# Cài cron job chạy tự động lúc 00:00 mỗi ngày
./log-archive --schedule <thư-mục-log>

# Gỡ cron job
./log-archive --unschedule
```

**Ví dụ:**

```bash
# Archive thư mục /var/log/nginx
./log-archive /var/log/nginx

# Lên lịch tự động mỗi đêm cho /var/log/nginx
./log-archive --schedule /var/log/nginx

# Hủy lịch đã cài
./log-archive --unschedule
```

## Ví dụ Output

```
[2026-05-09 00:00:01] Archived '/var/log/nginx' -> '/root/log-archives/logs_archive_20260509_000001.tar.gz'
```

File archive được lưu tại `~/log-archives/` với tên theo định dạng:

```
logs_archive_YYYYMMDD_HHMMSS.tar.gz
```

Lịch sử các lần archive được ghi vào:

```
~/log-archives/archive.log
```

## Cấu trúc project

```
log-archive/
├── log-archive   # Script chính
└── README.md     # Tài liệu này
```
