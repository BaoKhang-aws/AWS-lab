+++
title = "Cài đặt Grafana"
date = 2020-05-14T00:38:32+07:00
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

**Nội dung**  
Các bước thực hiện:
- [Bước 1: Cài đặt Grafana lên Amazon EC2](#bước-1-cài-đặt-grafana-lên-amazon-ec2)
- [Bước 2: Testing Grafana](#bước-2-testing-grafana)

#### Bước 1: Cài đặt Grafana lên Amazon EC2

* SSH vào Grafana EC2 Instance. Giả sử IP **34.201.20.216**

```bash
 ssh ec2-user@34.201.20.216 -i GrafanaKeyPair.pem
```

* Do đây là lần đầu ta truy cập EC2 Instance chúng ta cần thực hiện cài đặt các cập nhật mới nhất.

```bash
sudo yum update -y
```

* Nhập vào cửa sổ terminal tập lệnh sau để cài đặt Grafana phiên bản mới. 

```bash
wget https://dl.grafana.com/oss/release/grafana-7.5.5-1.x86_64.rpm
sudo yum install grafana-7.5.5-1.x86_64.rpm
```

* Sau khi cài đặt dịch vụ Grafana, bật dịch vụ Grafana bằng tập lệnh sau. 

```bash
sudo systemctl daemon-reload
sudo systemctl start grafana-server
sudo systemctl status grafana-server
```

* Khởi động dịch vụ cùng máy chủ bằng tập lệnh sau.

```bash
sudo systemctl enable grafana-server
```

* Truy cập Grafana server theo đường dẫn sau với account admin-admin để bắt đầu cấu hình. 

```bash
https://<Public-IP-Grafana-Server>:3000

  ######## Omitted

Installed:
  grafana.x86_64 0:7.5.5-1

Dependency Installed:
  dejavu-fonts-common.noarch 0:2.33-6.amzn2         dejavu-sans-fonts.noarch 0:2.33-6.amzn2         fontconfig.x86_64 0:2.13.0-4.3.amzn2              fontpackages-filesystem.noarch 0:1.44-8.amzn2
  libfontenc.x86_64 0:1.1.3-3.amzn2.0.2             urw-fonts.noarch 0:2.4-16.amzn2                 xorg-x11-font-utils.x86_64 1:7.5-21.amzn2

Complete!
```

* Reload lại dịch vụ systemd để nạp các cài đặt mới. Khởi chạy Grafana Server, rồi kiểm tra status.

```bash
sudo systemctl daemon-reload
```

* Chạy Grafana Server.

```bash
sudo systemctl start grafana-server
```

* Kiểm tra trạng thái của Grafana Server. Trạng thái đầu ra sẽ cho biết grafana-server đang active (running).

```bash
sudo systemctl status grafana-server
```

* Chạy lệnh bên dưới để đảm bảo Grafana sẽ luôn tự khởi chạy mỗi lần khởi động lại Amazon Linux 2 instance.

```bash
sudo systemctl enable grafana-server.service
```

* Kết quả như bên dưới

```bash
[ec2-user@ip-10-1-1-193 ~]$ sudo systemctl daemon-reload
[ec2-user@ip-10-1-1-193 ~]$ sudo systemctl start grafana-server
[ec2-user@ip-10-1-1-193 ~]$ sudo systemctl status grafana-server
● grafana-server.service - Grafana instance
   Loaded: loaded (/usr/lib/systemd/system/grafana-server.service; disabled; vendor preset: disabled)
   Active: active (running) since Wed 2020-09-09 17:22:31 UTC; 1min 34s ago
     Docs: http://docs.grafana.org
 Main PID: 32566 (grafana-server)
   CGroup: /system.slice/grafana-server.service
           └─32566 /usr/sbin/grafana-server --config=/etc/grafana/grafana.ini --pidfile=/var/run/grafana/grafana-server.pid --packaging=rpm cfg:default.paths.logs=/var/log/grafana cfg:default.paths.data=...

Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="Executing migration" logger=migrator id="add unique index user_auth_token.auth_token"
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="Executing migration" logger=migrator id="add unique index user_auth_token.prev_auth_token"
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="Executing migration" logger=migrator id="create cache_data table"
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="Executing migration" logger=migrator id="add unique index cache_data.cache_key"
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="Created default admin" logger=sqlstore user=admin
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="Starting plugin search" logger=plugins
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="Registering plugin" logger=plugins name="Direct Input"
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="External plugins directory created" logger=plugins directory=/var/lib/grafana/plugins
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal systemd[1]: Started Grafana instance.
Sep 09 17:22:31 ip-10-1-1-193.ec2.internal grafana-server[32566]: t=2020-09-09T17:22:31+0000 lvl=info msg="HTTP Server Listen" logger=http.server address=[::]:3000 protocol=http subUrl= socket=
[ec2-user@ip-10-1-1-193 ~]$ sudo systemctl enable grafana-server.service
Created symlink from /etc/systemd/system/multi-user.target.wants/grafana-server.service to /usr/lib/systemd/system/grafana-server.service.
```

#### Bước 2: Testing Grafana

* Kiểm tra Grafana Server mới được cài đặt bằng cách truy cập địa chỉ Public IP của Grafana EC2 Instance thông qua port 3000.

```bash
18.206.59.38:3000
```

* Nó sẽ điều hướng tới trang login của Grafana. Sử dụng tài khoản mặc định với **username** and **password** như bên dưới.
  * **Username**:	`admin`
  * **Password**: `admin`

![2](/images/Firsttime-login-Grafana.PNG?width=30pc)

* Sau khi login Grafana, phần mềm sẽ yêu cầu thay đổi admin password.Nhập password mới (except admin) rồi bấm **Save**. 

![2](/images/Change-Gra-pass.PNG?width=30pc)

* Tại trang chủ chúng ta có thể bắt đầu với việc thêm Data Sources, Dashboards, sử dụng Users or Explore plugins và hơn thế nữa.

![2](/images/grafana-landing.PNG?width=100pc)
