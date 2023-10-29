# Quản lý tiến trình trên MacOS

Danh mục

* [Tìm và đóng cổng đang hoạt động](#tìm-và-đóng-cổng-đang-hoạt-động)

### Tìm và đóng cổng đang hoạt động

Lệnh `lsof` (List Open Files) trên Mac OS cho chúng ta danh sách các tiến trình đang chạy và danh sách các file, cổng đang sử dụng.

Ví dụ: để kiểm tra xem có tiến trình nào đang sử dụng cổng `9000` không? Chúng ta chạy lệnh:

```bash
lsof -i :9000
```

Kết quả (nếu có):

```bash
COMMAND   PID   USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
java    18886 sidd88  382u  IPv6 0x514a9b7ec268915b      0t0  TCP *:cslistener (LISTEN)
```

Để đóng tiến, chúng ta sử dụng lệnh `kill [PID]`.

Ở ví dụ trên, chúng ta thấy đang có 1 tiến trình sử dụng cổng `9000` với `PID` là `18886`. Để đóng tiến trình này, chúng ta chạy lệnh:
```bash
kill -9 18886
```

Các tham số của lệnh kill:
* `9`: đóng tiến trình ngay lập tức, tiến trình này sẽ không tự dọn dẹp (clean up) được. Điều này có thể xảy ra vấn đề. Chỉ nên sử dụng khi máy tính của bạn bị treo.
* `15` (TERM), `3` (QUIT): tiến trình sẽ `clean up` trước khi đóng.