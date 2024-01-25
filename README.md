
[SVTECH] Pre-Interview Test_SRE Position

Ứng viên: Triệu Xuân Hùng

1. Viết script để cài đặt base server cho môi trường production
- Công cụ sử dụng: Ansible

- Các thành phần đã triển khai:
    - Cấu hình timezone về UTC+7
    - User: "sysadmin"
    - Cấu hình để chặn login trực tiếp vào user root
    - Hostname: "test-server"
    - Cài đặt docker bằng gói apt docker.io
    - Cấu hình logging driver là json-file và storage driver là overlay2
    - Cấu hình file sysctl.conf để tối ưu mạng
    - Cài đặt và cấu hình auditd để log các command của người dùng
    - Cấu hình sshd để chặn xác thực bằng mật khẩu

- Các task của ansible:
    - Set timezone to UTC+7
    - Add user "Sysadmin"
    - Disable login for the root user
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
    - Disable password-based ssh
    - Restart sshd

- Hướng dẫn chạy:
    - Sửa địa chỉ trong file inventory thành địa chỉ máy chủ phù hợp
    - Sửa file /etc/ansible/ansible.cfg, thêm các dòng sau vào khối [defaults]:

        inventory      = /path-to-repo/inventory
        roles_path    = /path-to-repo/roles    
      Với /path-to-repo/ là đường dẫn trực tiếp đến repository này
    - Chạy playbook với lệnh:
    
        ansible-playbook /path-to-repo/playbook.yaml


2. Hệ thống monitor

- Để  theo dõi mức sử dụng tài nguyên của một tech stack, cần một số thành phần sau:
    - Thành phần thu thập dữ liệu: Thu thập các dữ liệu thô về mức sử dụng tài nguyên của các thành phần trong tech stack
    - Thành phần tổng hợp dữ liệu: Tổng hợp dữ liệu từ nhiều nguồn khác nhau 
    - Thành phần lưu trữ: Lưu trữ lại các dữ liệu để phục vụ cho phân tích
    - Thành phần trực quan hóa và phân tích: Biểu diễn các dữ liệu dưới dạng dễ hình dung và có ý nghĩa
    - Thành phần cảnh báo: Chủ động thông báo các vấn đề hoặc sự bất thường

- Hệ thống monitor ứng viên từng triển khai:

  Node Exporter --> Prometheus --> Victoria Metric --> Grafana --> Slack

  Vai trò của từng thành phần:

  - Node exporter: Được cài đặt trên tất cả các node làm nhiệm vụ thu thập dữ liệu để gửi thông tin lên Promethues
  - Promethues: Lấy dữ liệu từ Node exporter và lưu trữ dữ liệu
  - Victoria metrics: Thu thập dữ liệu từ Promethues, lưu trữ. Việc này làm dữ liệu luôn có tính HA, không bị mất nếu Prometheus xảy ra vấn đề.
  - Grafana: Truy suất dữ liệu từ victoria metrics và hiển thị trên dasboard. Gửi alert về cho Slack khi được cấu hình.
  - Slack: kênh thông tin với người dùng
 

