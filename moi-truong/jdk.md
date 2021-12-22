# Cài đặt JDK và chuyển đổi phiên bản JDK trên MacOS

JDK (Java Development Kit) bộ phần mềm cung cấp môi trường phát triển ứng dụng viết bằng ngôn ngữ Java.

Có thể cài đặt JDK bằng `Homebrew`, hoặc cài đặt thủ công. Bài viết này sẽ hướng dẫn cài đặt JDK bằng `Homebrew`.

## 1. Cài đặt JDK

Trước khi thực hiện cài đặt, chúng ta thực hiện update các gói và Homebrew phiên bản mới nhất.

```bash
brew update
```

### 1.1 Cài đặt JDK phiên bản mới nhất

#### Tìm kiếm gói java
  ```bash
% brew search java
--------------------------------------------------
==> Formulae
app-engine-java         java ✔                  java11                  javarepl                libreadline-java
google-java-format      java-service-wrapper    javacc                  jslint4java             pdftk-java
```

#### Thông tin chi tiết gói java

```bash
% brew info java
--------------------------------------------------
openjdk: stable 18.0.2 (bottled) [keg-only]
Development kit for the Java programming language
https://openjdk.java.net/
/usr/local/Cellar/openjdk/18.0.2 (641 files, 307.7MB)
  Poured from bottle on 2022-08-12 at 02:29:16
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/openjdk.rb
License: GPL-2.0-only with Classpath-exception-2.0
```

```bash
% brew info java11
--------------------------------------------------
openjdk@11: stable 11.0.16.1 (bottled) [keg-only]
Development kit for the Java programming language
https://openjdk.java.net/
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/openjdk@11.rb
License: GPL-2.0-only
```
#### Cài đặt gói java

```bash
% brew install java
```

#### Cấu hình

Mặc định, gói java là [keg-only](https://docs.brew.sh/FAQ#what-does-keg-only-mean), điều này có nghĩa là nó được cài đặt vào `/usr/local/Cellar` và không được liên kết vào các thư mục như `/usr/local/bin`, `/Library/Java/JavaVirtualMachines` hay `/usr/bin/java`.

Để `/usr/bin/java` wrapper tìm được bản JDK đã cài đặt, chúng ta sẽ tạo một liên kết đến `/Library/Java/JavaVirtualMachines/.`

```bash
% sudo ln -sfn /usr/local/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

Xác nhận liên kết thành công
```bash
% java -version
--------------------------------------------------
openjdk version "18.0.2" 2022-07-19
OpenJDK Runtime Environment Homebrew (build 18.0.2+0)
OpenJDK 64-Bit Server VM Homebrew (build 18.0.2+0, mixed mode, sharing)
```

### 1.2 Cài đặt JDK phiên bản 11

```bash
# Cài đặt gói java11
% brew install java11

# Tạo liên kết để Java wrappers tìm thấy SDK
% sudo ln -sfn /usr/local/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-11.jdk
```

### 1.3 Cài đặt JDK phiên bản 8

#### Tìm kiếm JDK 8

Như đã thực hiện ở bước trên, khi chạy `brew search java` sẽ không có gói `java8`.

Java 8 nằm trong gói `openjdk@8`. `openjdk` là giống với `java`, nó luôn luôn bao gồm phiên bản JDK mới nhất. Do vậy, chúng ta có thể cài java bản mới nhất, hoặc java 11 từ gói `openjdk`.

```bash
% brew search openjdk
--------------------------------------------------
==> Formulae
openjdk ✔                  openjdk@17                 openj9
openjdk@11 ✔               openjdk@8                  openvdb
```

#### Cài đặt JDK 8

```bash
# Cài đặt Java 8
% brew install openjdk@8
# Tạo liên kết để Java wrappers tìm thấy SDK
% sudo ln -sfn /usr/local/opt/openjdk@8/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-8.jdk
```

## 2. Đổi phiên bản JDK

Trong quá trình phát triển phần mềm, chúng ta có thể cần sử dụng các phiên bản JDK khác nhau tại mỗi thời điểm. Do vậy, cần chuyển giữa các phiên bản JDK đã cài đặt trên máy.

### 2.1 Kiểm tra các phiên bản JDK đã cài đặt

```bash
% /usr/libexec/java_home -V
--------------------------------------------------
Matching Java Virtual Machines (4):
    18.0.2 (x86_64) "Homebrew" - "OpenJDK 18.0.2" /usr/local/Cellar/openjdk/18.0.2/libexec/openjdk.jdk/Contents/Home
    17.0.4 (x86_64) "Homebrew" - "OpenJDK 17.0.4" /usr/local/Cellar/openjdk@17/17.0.4/libexec/openjdk.jdk/Contents/Home
    11.0.16.1 (x86_64) "Homebrew" - "OpenJDK 11.0.16.1" /usr/local/Cellar/openjdk@11/11.0.16.1/libexec/openjdk.jdk/Contents/Home
    1.8.0_345 (x86_64) "Homebrew" - "OpenJDK 8" /usr/local/Cellar/openjdk@8/1.8.0+345/libexec/openjdk.jdk/Contents/Home
/usr/local/Cellar/openjdk/18.0.2/libexec/openjdk.jdk/Contents/Home

% ls -lsah /Library/Java/JavaVirtualMachines/ 
--------------------------------------------------
openjdk-11.jdk  -> /usr/local/opt/openjdk@11/libexec/openjdk.jdk
openjdk-17.jdk  -> /usr/local/opt/openjdk@17/libexec/openjdk.jdk
openjdk-8.jdk   -> /usr/local/opt/openjdk@8/libexec/openjdk.jdk
openjdk.jdk     -> /usr/local/opt/openjdk/libexec/openjdk.jdk
```

### 2.2 Chuyển đổi phiên bản JDK

Để thực hiển chuyển đổi, chúng ta thêm `bash function` dưới vào `~/.zshrc` (MacOS phiên bản 10.15 trở lên), hoặc `~/.bashrc` (Mac OS phiên bản thấp hơn 10.15).

```bash
~/.zshrc
--------------------------------------------------
jdk() {
  version=$1
  unset JAVA_HOME;
  export JAVA_HOME=$(/usr/libexec/java_home -v"$version");
  java -version
}
```

Gọi `bash function` để chuyển phiên bản JDK

```bash
% java -version
--------------------------------------------------
openjdk version "18.0.2" 2022-07-19
OpenJDK Runtime Environment Homebrew (build 18.0.2+0)
OpenJDK 64-Bit Server VM Homebrew (build 18.0.2+0, mixed mode, sharing)

% jdk 17
--------------------------------------------------
openjdk version "17.0.4" 2022-07-19
OpenJDK Runtime Environment Homebrew (build 17.0.4+0)
OpenJDK 64-Bit Server VM Homebrew (build 17.0.4+0, mixed mode, sharing)

% jdk 11
--------------------------------------------------
openjdk version "11.0.16.1" 2022-08-12
OpenJDK Runtime Environment Homebrew (build 11.0.16.1+0)
OpenJDK 64-Bit Server VM Homebrew (build 11.0.16.1+0, mixed mode)

% jdk 1.8
--------------------------------------------------
openjdk version "1.8.0_345"
OpenJDK Runtime Environment (build 1.8.0_345-bre_2022_08_04_23_35-b00)
OpenJDK 64-Bit Server VM (build 25.345-b00, mixed mode)
```