
```
sudo wget http://dn-repo.fsoft.com.vn/setup/installrepo.sh
sudo chmod 777 installrepo.sh
sudo ./installrepo.sh

```

1. Trỏ Repo về DN

```
sudo su
```

2. Tải bộ cài

```
sudo wget http://unix-repo-dn.fsoft.com.vn/setup/installrepo.sh
```

3. Cấp quyền bộ cài
```
sudo chmod 777 installrepo.sh
```

4. Cài đặt

```
sudo ./installrepo.sh
```

5. Cài đặt ntpdate

```
sudo apt-get install ntpdate
```

6. Update ngày giờ

```
sudo ntpdate 10.133.79.7
```

7. Tắt firewall & update app

```
sudo service ufw stop
sudo apt update -y
```

8. Đặt pass cho root

```
passwd root
Đặt pass là: sU@F$0ft.com.vn

it.fdn
WFH@12345
```