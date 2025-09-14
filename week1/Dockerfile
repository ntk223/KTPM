FROM ubuntu:20.04

# Cập nhật danh sách package, cài OpenSSH và sudo
RUN apt-get update && apt-get install -y openssh-server sudo

# Tạo thư mục cần thiết cho SSH
RUN mkdir /var/run/sshd

# Thiết lập mật khẩu cho user root là 'root'
# Khi chạy container có thể login bằng ssh root@<container_ip> với mật khẩu là 'root'
RUN echo 'root:root' | chpasswd


# Tạo user mới user1 với mật khẩu là 'user1' và thêm user này vào nhóm sudo
RUN useradd -ms /bin/bash user1 && echo 'user1:user1' | chpasswd && adduser user1 sudo


# Khai báo image sẽ mở cổng 22
EXPOSE 22


# Lệnh mặc định khi container cháy
CMD ["/usr/sbin/sshd","-D"]