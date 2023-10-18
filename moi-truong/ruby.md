# Cài đặt Ruby trên MacOS với rbenv

Mặc định trên MacOS đã có cài đặt sẵn Ruby, tuy nhiên phiên bản khá thấp (ở thời điểm hiện tại 10/2023 là phiên bản 2.6.0), dẫn đến việc cài các phần mềm khác không tương thích phiên bản (ví dụ như Cocoapods...)

Rbenv sinh ra giúp bạn giải quyết vấn đề này.

## Cài đặt rbenv

Để cài đặt `rbenv`, bạn chạy lệnh (yêu cầu phải cài đặt `Homebrew` trước đó):

```bash
brew install rbenv
```

## Cài đặt ruby

### Kiểm tra danh sách các phiên bản

Kiểm tra các phiên bản ruby:

```bash
rbenv install --list
```

### Cài đặt ruby

Cài đặt ruby
```bash
rbenv install <version>
```
Ví dụ:
```bash
rbenv install 3.1.4
```

### Cấu hình

Cấu hình để hệ thống nhận phiên bản Ruby của rbenv
```bash
echo 'eval "$(rbenv init -)"' >> ~/.zshrc
```

### Chuyển đổi phiên bản

Để sử dụng phiên bản Ruby cho toàn bộ máy, chạy lệnh:
```bash
rbenv global <version>
```

Để sử dụng local cho từng thư mục:
```bash
rbenv local <version>
```

## Kết luận

Với `rbenv`, việc quản lý, chuyển đổi phiên bản Ruby trên máy tính của bạn đã dễ dàng hơn.