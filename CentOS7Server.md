<div align="center">

# CENTOS 7 SERVER

</div>

# 1. Update hệ thống
- sudo sed -i 's|mirrorlist=|#mirrorlist=|g' /etc/yum.repos.d/CentOS-*.repo
- sudo sed -i 's|#baseurl=|baseurl=|g' /etc/yum.repos.d/CentOS-*.repo
- sudo sed -i 's|mirror.centos.org|vault.centos.org|g' /etc/yum.repos.d/CentOS-*.repo
- sudo yum clean all
- sudo yum makecache
- sudo yum update -y

# 2. Install git
- sudo yum install git

# 3. Install Docker
## Bước 1: Gỡ Docker cũ (nếu có)
- sudo yum remove docker docker-common docker-selinux docker-engine
## Bước 2: Cài đặt các gói cần thiết
- sudo yum install -y yum-utils device-mapper-persistent-data lvm2
## Bước 3: Thêm repository Docker chính thức
- sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
## Bước 4: Cài đặt Docker
- sudo yum install -y docker-ce docker-ce-cli containerd.io
## Bước 5: Khởi động và kích hoạt Docker
- sudo systemctl start docker
- sudo systemctl enable docker
## Bước 6: Kiểm tra Docker hoạt động chưa
- sudo docker --version
- sudo docker run hello-world
## (Tuỳ chọn) Bỏ sudo khi chạy Docker
- sudo usermod -aG docker $USER