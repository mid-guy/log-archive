# Log Archive

Bash script tương tác để nén và lưu trữ log thành file `.tar.gz` có timestamp — hỗ trợ lọc theo số ngày, tự động dọn archive cũ, và cài cron job chạy mỗi đêm.

## Tính năng

| Mục | Mô tả |
|-----|-------|
| Interactive CLI | Menu hướng dẫn từng bước qua terminal |
| Archive theo tuổi file | Chỉ nén các file log cũ hơn N ngày |
| Tự động dọn archive | Xóa các bản archive cũ hơn N ngày |
| Ghi log hoạt động | Mỗi lần archive được ghi vào `~/log-archives/archive.log` |
| Cron tùy chọn | Hỏi cài cron job sau mỗi lần chạy |

## Yêu cầu

- Bash >= 4
- `tar`, `find`, `date`, `crontab` — có sẵn trên mọi hệ thống Unix/Linux/macOS

## Chạy nhanh (không cần cài đặt)

```bash
bash <(curl -s https://raw.githubusercontent.com/mid-guy/log-archive/main/log-archive)
```

## Cài đặt thủ công

```bash
curl -O https://raw.githubusercontent.com/mid-guy/log-archive/main/log-archive
chmod +x log-archive
sudo mv log-archive /usr/local/bin/log-archive
```

Sau đó chạy từ bất kỳ đâu:

```bash
log-archive
```

## Sử dụng

Sau khi khởi động, script hiển thị menu:

```
=== Log Archive Tool ===
1. Chọn thư mục log        [chưa chọn]
2. Số ngày giữ log          [7]
3. Số ngày giữ bản archive  [30]
4. Chạy archive
5. Thoát
```

1. Chọn **1** để nhập thư mục log (mặc định `/var/log`)
2. Chọn **2** để chỉnh số ngày giữ log (mặc định 7)
3. Chọn **3** để chỉnh số ngày giữ archive (mặc định 30)
4. Chọn **4** để chạy — script sẽ hỏi có muốn cài cron không

## Ví dụ Output

```
[2026-05-09 00:00:01] Archived '/var/log' (files older than 7d) -> '/root/log-archives/logs_archive_20260509_000001.tar.gz'
Đã xóa các bản archive cũ hơn 30 ngày.
```

## Cấu trúc project

```
log-archive/
├── log-archive   # Script chính
└── README.md     # Tài liệu này
```

## Nguồn tham khảo

Project này được xây dựng dựa trên yêu cầu từ [roadmap.sh](https://roadmap.sh/projects/log-archive-tool).
