1      **Cấu hình trỏ update đến server Repo tại FDN.**

```echo

wget [_http://dn-repo.fsoft.com.vn/setup/installrepo.sh_](http://unix-repo-dn.fsoft.com.vn/setup/installrepo.sh)

chmod 777 installrepo.sh  
./installrepo.sh
```

chạy xong sẽ có thông báo đã trỏ về Repo FDN

2      **Đồng bộ thời gian với máy chủ domain FDN:**

+Cài đặt ntpdate Tool:

_apt-get install ntpdate_

+Thực hiện update ngày từ AD:

_ntpdate 10.133.79.6_

_timedatectl set-timezone Asia/Ho_Chi_Minh_

3      **Cấu hình Chính sách :**

Tắt Firewall, gõ lệnh:  _service ufw stop_

4      **Cấu hình SSH:**

**A. Cấm SSH bằng account Root:**

+ Cài đặt SSH Server:        _apt-get install openssh-server_

          + Cấm SSH bằng account root. Đổi PermitRootLogin yes thành no , bằng lệnh:

_sed -i '/#PermitRootLogin yes/c\PermitRootLogin no' /etc/ssh/sshd_config_

**B. Đổi port mặc định khi SSH đến máy linux.**

+ Đổi dòng cấu hình Port 22 và đổi thành 2345, bằng lệnh:

_sed -i '/Port 22/c\Port 2345' /etc/ssh/sshd_config_

+ Restart lại dịch vụ SSH, bằng lệnh:

_service sshd restart_

5      **Tạo Account:**

**A. Đổi Pass Root Account:**

Chạy lệnh passwd root. Nhập pass root (Pass Root do IT giữ. Liên hệ a QuanPN1 / TuanPA3 / TungNT35)

_passwd root_ _//_[2!T@F$0ft.com.vn](mailto:2!T@F$0ft.com.vn)

///Đặt pass là: sU@F$0ft.com.vn

**B. Tạo Account**  itfdn.root:

+ Tạo account: _useradd -m itfdn.root_

                     _passwd itfdn.root_

itfdn.root/XXX: WFH@12345

**C. Cấp quyền Sudo / Root cho các account vừa tạo:**

+ Mở file sudoers. Bằng lệnh: nano /etc/sudoers

+ Ta sẽ add group sudo cho 2 account: itfdn.root và daiht1. Giờ ta sẽ check group sudo đã có quyền admin chưa.

+ Mở file sudoers:  _nano /etc/sudoers_

+ Tìm xem có dòng: _%sudo        ALL= (ALL)         ALL_

Nếu không có thì thêm vào và Lưu file lại.

6      **Install Agent/Endpoint McAfee on Linux**

A        **CHUẨN BỊ GÓI CÀI**

+ Sử dụng lệnh Wget để copy file về máy linux, copy nội dung sau vào terminal:

_cd /_

_mkdir software_

_cd /software_

_wget --no-check-certificate https://fdn-support.fsoft.com.vn/public/Network/IT-Tools/ePOAgent/Linux/5.7/install.sh_

_wget --no-check-certificate https://fdn-support.fsoft.com.vn/public/Network/IT-Tools/ePOAgent/Linux/5.7/installdeb.sh_

_wget --no-check-certificate https://fdn-support.fsoft.com.vn/public/Network/IT-Tools/ePOAgent/Linux/5.7/installrpm.sh_

_wget --no-check-certificate https://fdn-support.fsoft.com.vn/public/Network/IT-Tools/ePOAgent/EndpointSecurity/Linux/10.7/install-mfetp.sh_

_wget --no-check-certificate https://fdn-support.fsoft.com.vn/public/Network/IT-Tools/ePOAgent/EndpointSecurity/Linux/10.7/McAfeeTP-10.7.3-46-standalone.linux.tar.gz_

**+** Cấp quyền thực thi cho file Cài đặt:

_chmod 777 /software/install*_

B        **CÀI ĐẶT AGENT MCAFEE**

+ Thực hiện cài đặt:

_cd /software_

_./install.sh -i_

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image002.gif)

                                    _**Quá trình cài đặt thành công**_

**+** Restart lại dịch vụ      _/etc/init.d/cma restart_

**+** Lệnh kiểm tra tình trạng Agent       _/etc/init.d/cma status_

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image004.jpg)

+ Lệnh kiểm tra thông tin version agent, server EPO kết nối

_cd /opt/McAfee/agent/bin/_

_./cmdagent -i_

      + Để xem các lệnh khác ta gõ:           ./cmdagent –h

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image006.jpg)

C        **CÀI ĐẶT ENDPOINT**

**+** Chạy lệnh cài đặt:       _/software/install-mfetp.sh_

+ Phần mềm sẽ chạy tự động, cài đặt thành công sẽ hiện ra như bên dưới:

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image008.jpg)

D        **Force update trên máy Client**

**+** Gõ lệnh force update:    

**_cd /opt/McAfee/ens/tp/bin_**

**_./mfetpcli --runtask --index 3_**

**+** Kiểm tra update:

           ![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image010.jpg)

                               _Update thành công._

+ Kiểm tra các task chạy của ENS

 _./mfetpcli --listtask_

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image012.jpg)

**+ Quét AV full scan:**

 **cd /opt/McAfee/ens/tp/bin/**

 **./mfetpcli --runtask --index 2**

Kiểm tra log full scan:

7      **Install Agent Nac  
  
**

**_cd /software_**

**+** Có thể thực hiện cài đặt bằng cách copy đoạn lệnh dưới vào Terminal khi SSH:

[](http://10.133.79.149/linux/10.133.79.149permanent/SecureConnectorLinuxInstall.sh)

_wget_ [https://fdn-support.fsoft.com.vn/public/Network/IT-Tools/CounterACT/Linux/ForeScoutSecureConnector_64_not_visible_daemon.tar.gz](https://fdn-support.fsoft.com.vn/public/Network/IT-Tools/CounterACT/Linux/ForeScoutSecureConnector_64_not_visible_daemon.tar.gz)_  
tar -zxvf ForeScoutSecureConnector_64_not_visible_daemon.tar.gz  
cd secure_connector/  
chmod 777 install.sh  
,/install.sh  
systemctl enable secureconnector.service  
systemctl start secureconnector.service_

   _+_Lệnh kiểm  tra sau khi cài đặt :

_ps aux | less | grep SecureConnector_

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image014.jpg)

                                    _NAC Agent đã cài đặt thành công._

8      **Install Agent Ivanti**

**Supported Linux Operating Systems**

**Supported Operating Systems** 

**Supported Editions**

CentOS Linux 5.5-7.x

Oracle Enterprise Linux 5.5-7.x

Red Hat Enterprise Linux 5.5-7.x 

Server

SUSE Linux Enterprise 10 SP2-12

• Desktop  
• Server

Ubuntu Linux 14.04 LTS, 16.04 LTS 

• Desktop  
• Server

**Yêu cầu:**

Java Runtime Environment (JRE)7 or later

 Kiểm tra version: Open Terminal type : java -version

Trường hợp chưa cài đặt hoặc version java cũ cần download & install tại [https://www.java.com/en/download/](https://www.java.com/en/download/)

 Cài đặt java: _apt **install** openjdk-8-jre-headless  (ubuntu 18.04 thì cài java 8)_

 ![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image016.jpg)

**Install:**

**Step**

**Description**

**1**

**Tạo folder lưu agent cài đặt**

cd /  
mkdir ivanti  
cd ivanti/

**2**

**Copy agent vào máy cần cài**

[](http://unix-repo-dn.fsoft.com.vn/software/ivanti/patchagent.tar)

wget [https://dn-repo.fsoft.com.vn/software/ivanti/install](https://dn-repo.fsoft.com.vn/software/ivanti/install)wget [https://dn-repo.fsoft.com.vn/software/ivanti/patchagent.properties](https://dn-repo.fsoft.com.vn/software/ivanti/patchagent.properties)  
wget https://dn-repo.fsoft.com.vn/software/ivanti/patchagent.tar

**3**

**Install:**  
  
cd ivanti/  
chmod 777 install  
  
./install -silent -d /usr/local/ -p https://ivanti-dn01.fsoft.com.vn -sno 3B50674E-A31D97CD -g support  
  
====> Cài đặt thành công message báo như hình bên dưới

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image018.gif)

9         **Join doamin:**

**Step 1**. Đặt tên máy cần join domain (như hình dưới)

sudo nano /etc/hosts  
edit Computer name owner

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image020.jpg)

hostnamectl set-hostname [computer name]  
Change đúng hostname thực hiện reboot

sudo reboot  

**Step 2**. Kiểm tra & add DNS server ( như hình dưới) 

nano /etc/resolv.conf

Add 2 dòng dưới vào file cấu hình

nameserver 10.133.79.9  
nameserver 10.133.79.8

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image022.jpg)

**Step3**. Trỏ update về Repo FDN

wget [http://unix-repo-dn.fsoft.com.vn/setup/installrepo.sh](http://unix-repo-dn.fsoft.com.vn/setup/installrepo.sh)

chmod 777 installrepo.sh

./installrepo.sh

p/s: nếu thực hiện rồi bỏ qua bước này

**Step4**. Cài đặt các gói yêu cầu ( như hình dưới)

apt-get update  
apt-get install realmd sssd samba-common samba-common-bin samba-libs sssd-tools krb5-user adcli packagekit vim -y

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image024.gif)

  
Trong khi gói được download & install sẽ hiển thị cửa sổ bên dưới để nhập tên domain **FSOFT.FPT.VN** (nhập chữ in hoa) & gõ Enter

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image026.jpg)

Tiếp theo get kerberos từ AD

kinit -V itdn.support04

**Step5**. Join domain (dùng account có quyền join domain)

realm --verbose join -U itdn.support04 [fsoft.fpt.vn](http://fsoft.fpt.vn/)

Sau khi gõ lệnh trên & yêu cầu nhập password xác nhận nếu nhận message trả về như dưới

 ![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image028.jpg)

Cách fix:

echo 'ad_hostname = **[Hostname]**.[fsoft.fpt.vn](http://fsoft.fpt.vn/)' >> /etc/sssd/sssd.conf  
echo 'dyndns_update = True' >> /etc/sssd/sssd.conf  
service sssd restart

**Step6**. Thay đổi định dạng login bằng account domain trên máy workstation

sudo nano /etc/sssd/sssd.conf

Nội dung file hiện tại như hình dưới

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image030.jpg)

Chỉnh sửa thành:

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image032.jpg)

**Step7**. Kiểm tra lại máy đã join được domain chưa ?

realm list

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image034.jpg)

Kiểm tra việc query được account/group từ domain **FSOFT.FPT.VN**

id [account name]

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image036.jpg)

**Step8**. Add quyền user vào group root local

Tạo group admin, phân quyền & add user vào group admin

groupadd administrators

usermod -a -G administrators itdn.support04   (ở ví dụ là account: quanpn1)

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image038.jpg)

Add quyền root cho account itfdn.root & group administrator tại vị trí file bên dưới.

visudo

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image040.jpg)

Ctrl +x (lưu & thoát)

**Add quyền user tự động tạo profile_folder:**  
nano /etc/pam.d/common-account

**Add thêm dòng:** 

session    required   pam_mkhomedir.so skel=/etc/skel/ umask=0022

**Step 9**. Login account domain

 + Login với ssh

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image042.jpg)

+ Login với GUI

![](file:///C:/Users/duydq5/AppData/Local/Temp/msohtmlclip1/01/clip_image044.jpg)