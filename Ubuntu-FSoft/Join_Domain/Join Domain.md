# Join Domain

---
### Nội dung
- Bao gồm các mục:
	- [ ] 1. Đặt tên máy cần join domain [[#1. Đặt tên máy]]
	- [ ] 2. Kiểm tra & add DNS server
	- [ ] 3. Trỏ update về Repo FDN
	- [ ] 4. Cài đặt các gói yêu cầu
	- [ ] 5. Join Domain
		- [ ] Add hostname đến Kerberos 
		- [ ] Joining a IPA domain
		- [ ] Login Account domain
	- [ ] 7. Kiểm tra Join Domain
	- [ ] 8. Add quyền user local
		- [ ] Tạo group admin
		- [ ] Add user vào group admin
		- [ ] Add quyền root
	- [ ] 9. Kiểm tra Login
		- [ ] Login với ssh
		- [ ] Login GUI

## 1. Đặt tên máy
- Xem nội dung file: [[Qui định đặt tên máy]]
- SSH hoặc mở console Terminal trên máy cần join domain

```echo
hostnamectl set-hostname [hostname]
```

- Mở file hosts cấu hình

```echo
sudo vi /etc/hosts

//hoặc
nano /etc/hosts
```

- Edit lại dòng số 2 : ==127.0.1.1.1	[hostname]==

![[ComputerName-hostname.png]]

- Lưu lại và khởi động lại máy.

```echo
//Khoi dong lai 
sudo reboot
```

## 2. Kiểm tra & add DNS server

- Mở file resolv.conf

```echo
nano /etc/resolv.conf

//Hoặc
vi /etc/resolv.conf
```

- Thêm 2 dòng dưới vào file cấu hình
>nameserver 10.133.79.7
nameserver 10.133.79.6

![[DNS.png]]

- Lưu lại file

## 3. Trỏ update về Repo FDN
- Nếu ở trên đã làm trỏ về Repo FDN rồi thì bỏ qua bước này.
- Nếu chưa làm thì thao tác, chạy các câu lệnh

```echo
wget [http://unix-repo-dn.fsoft.com.vn/setup/installrepo.sh](http://unix-repo-dn.fsoft.com.vn/setup/installrepo.sh)

chmod 777 installrepo.sh

./installrepo.sh
```


## 4. Cài đặt các gói yêu cầu
- Chạy update thư viện
- Cài đặt các gói phần mềm tiêu chuẩn như:
	- [[Realmd]] 
	- [[SSSD]] [Quick Start Guide - sssd.io](https://sssd.io/docs/quick-start.html)
	- sssd-tools 
	- samba-common [[Samba-common]]
	- samba-common-bin 
	- samba-libs 
	- krb5-user [Kerberos for Ubuntu | Documentation (ed.ac.uk)](https://computing.help.inf.ed.ac.uk/kerberos-ubuntu)
	- [[adcli]] [adcli - Easy Way To Join RHEL/CentOS System To Active Directory Domain | 2DayGeek](https://www.2daygeek.com/join-integrate-rhel-centos-linux-system-to-windows-active-directory-ad-domain/)
	- packagekit 
	- vim

```echo
apt-get update

apt-get install realmd sssd samba-common samba-common-bin samba-libs sssd-tools krb5-user adcli packagekit vim -y
```

![[install-package.png]]

- Trong khi gói được download & install sẽ hiển thị cửa sổ bên dưới để nhập tên domain **FSOFT.FPT.VN** (nhập chữ in hoa) & gõ Enter
> FSOFT.FPT.VN

![[check-Domain.png]]

## 5. Add hostname đến Kerberos từ AD

- Liên quan đến gói package **krb5-user** 
- Account join domain

```echo
//kinit -V [account join domain]
kinit -V quanpn1
```

![[kinit-kerberos.png]]

## 6. Joining a IPA domain
- Join domain (dùng account có quyền join domain)
- Gõ câu lệnh

```echo
realm --verbose join -U quanpn1 fsoft.fpt.vn
```

- Sau khi gõ lệnh trên & yêu cầu nhập password xác nhận nếu nhận message trả về như dưới

![[DNS_unsuccessful.png]]

- Nếu xuất hiện lỗi ở trên thì chạy lệnh

```echo
echo 'ad_hostname = [Hostname].fsoft.fpt.vn' >> /etc/sssd/sssd.conf

echo 'dyndns_update = True' >> /etc/sssd/sssd.conf  
service sssd restart
```

## 7. Login Account domain trên máy workstation
- Thay đổi định dạng login bằng account domain trên máy workstation

```echo
sudo vi /etc/sssd/sssd.conf

//hoặc
nano /etc/sssd/sssd.conf
```

- Nội dung file hiện tại như hình dưới

![[sssd_conf.png|600]]

- Chỉnh sửa thành

> use_fully_qualified_names = True -> use_fully_qualified_names = ==False==
fallback_homedir = /home/%d/%u -> fallback_homedir = ==/home/%u==

![[config_sssd-conf.png|400]]

## 8. Kiểm tra Join Domain thành công

- Kiểm tra lại máy đã join được domain chưa ?
- Chạy câu lệnh sau:

```echo
realm list
```

- Bảng hiển thị

![[check-join-domain.png|400]]

- Kiểm tra việc query được account/group từ domain **FSOFT.FPT.VN**
- Check 1 account thuộc domain fsoft

```echo
id [account name]
```

![[check-query-domain.png]]

- Khởi động lại máy

```echo
reboot
```


## 9. Add quyền user vào group root local
- Tạo group admin, phân quyền & add user vào group admin

```echo
// Tạo Group administrators
groupadd administrators

// Add user [account_name] vào Group administrators
usermod -a -G administrators [account_name]   

//(ở ví dụ là account: quanpn1)
usermod -a -G administrators quanpn1
```

![[groupadd-local01.png|400]]

- Add quyền root cho account ==itfdn.root== & group ==administrator== tại vị trí file bên dưới.

```echo
//Mở file khai báo
visudo
```

![[groupadd-local02.png|500]]

- Bấm Ctrl + x (Lưu file và thoát)
- Add quyền user tự động tạo ==profile_folder==:

```echo
vi /etc/pam.d/common-account

// Hoặc
nano /etc/pam.d/common-account
```

- Thêm dòng
> session	required	pam_mkhomedir.so	skel=/etc/skel/	umask=0022

- Bấm Ctrl + x (Lưu file và thoát)

## 10. Kiểm tra Login
### 10.1 . Login account domain
 - Login với ssh

![[Login-ssh.png]]

### 10.2 . Login GUI
- Đăng nhập vào user vào GUI

![[Login-GUI1.png]]

![[Login-GUI2.png]]

![[Login-GUI3.png]]

