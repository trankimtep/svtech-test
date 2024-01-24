
[SVTECH] Pre-Interview Test_SRE Position

Ứng viên: Triệu Xuân Hùng

1. Viết script để cài đặt base server cho môi trường production
- Công cụ sử dụng: Ansible
- Các thành phần đã triển khai:
    - User: "sysadmin"
    - Hostname: "test-server"
    - Cài đặt docker bằng gói apt docker.io
    - Cấu hình logging driver là json-file và storage driver là overlay2
    - Cấu hình file sysctl.conf để tối ưu mạng
    - Cài đặt và cấu hình auditd để log các command của người dùng

- Các task của ansible:
    - Add user "Sysadmin"
    - Change hostname
    - Update apt cache
    - Install Docker
    - Config Docker
    - Restart Docker service
    - Network config tuning
    - Reload sysctl
    - Install auditd
    - Backup auditd config
    - Config auditd
    - Restart auditd service

2. 
 

