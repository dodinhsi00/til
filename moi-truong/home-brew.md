# Cài đặt Homebrew

`Homebrew` là trình quản lý gói phần mềm mã nguồn mở cho MacOS, giúp việc cài đặt phần mềm dễ dàng hơn. Cài đặt `Homebrew` bằng cách mở `Terminal` và chạy lệnh:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Sau khi cài đặt xong, bạn có thể chạy lệnh `brew doctor` để đảm bảo mọi thứ đã được cài đặt đúng.

Mặc định (`Formulae`), các gói trong `Homebrew` sẽ chạy dưới dạng `services`, hoặc `cli` mà không có giao diện. 

Để cài đặt các ứng dụng có giao diện người dùng, chúng ta sử dụng `casks`. `Brew cask` là một tiện ích mở rộng của `Brew`, cho phép cài đặt một số ứng dụng có giao diện đồ hoạ (GUI). Để cài đặt `Cask`, chạy lệnh bên dưới:

```bash
brew install cask
```

Các lệnh cơ bản

```bash
# Mở trang chủ HomeBrew
brew home
# Hiển thị các package đã cài đặt
brew list
# Hiển thị các casks package đã cài đặt
brew list --casks
# Hiện thêm thông tin package
brew info <package_name>

# Cài đặt package
brew install <package_name>
# Cài đặt casks package
brew cask install <package_name>
# Gỡ bỏ package đã cài đặt
brew uninstall <package_name>

# Tìm kiếm package với keyword
brew search <keyword>
# Tìm kiếm casks package với keyword
brew search --casks <keyword>
# Tìm kiếm package với mô tả chi tiết
brew search <keyword> --desc ''
# Tìm kiếm casks package với mô tả chi tiết
brew search --casks <keyword> --desc ''

# Cập nhật brew package và chính homebrew
brew update
# Hiển thị những brew đã bị lỗi thời
brew outdated
# Cập nhật package đã cài đặt
brew upgrade <package_name>
# Cập nhật tất cả các gói đã cài đặt
brew upgrade
# Xoá các gói không dùng đến
brew cleanup
```

Một số lệnh quản lý dịch vụ

```bash
# Liệt kê tất cả các dịch vụ quản lý bởi brew services
brew services list
# Thiết lập một dịch vụ chạy cùng hệ thống (ví dụ mysql)
brew services start mysql
# Khởi chạy một dịch vụ (ví dụ mysql)
brew services run mysql
# Dừng một dịch vụ đang chạy (ví dụ mysql)
brew services stop mysql
# Khởi động lại dịch vụ (ví dụ mysql)
brew services restart mysql
# Dọn dẹp cách dịch vụ không dùng đến
brew services cleanup
```