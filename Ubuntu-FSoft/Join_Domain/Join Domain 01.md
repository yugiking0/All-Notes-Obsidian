

```cmd
hostnamectl set-hostname [hostname]
nano /etc/hosts
 sua dong so 2 
127.0.1.1.1	[hostname]
Luu lai
sau do go reboot
kiem tra cau hinh dns

nano /etc/resolv.conf

them 2 dong
nameserver 10.133.79.7
nameserver 10.133.79.6

luu lai

apt-get update
apt-get install realmd samba-common samba-common-bin samba-libs sssd-tools krb5-user adcli packagekit vim -y

hien bang thi go ( viet hoa)
FSOFT.FPT.VN
ok

kinit -V [account join domain]

realm --verbose join -U [account join domain] fsoft.fpt.vn

nano /etc/sssd/sssd.conf
sua lai

use_fully_qualified_names = True -> use_fully_qualified_names = False
fallback_homedir = /home/%d/%u -> fallback_homedir = /home/%u

Luu Lai
check da  join domain chua

realm list

check 1 account thuoc domain fsoft
reboot

id [account]

nano /etc/pam.d/common-account

them dong

session	required	pam_mkhomedir.so	skel=/etc/skel/	umask=0022
Luu lai

adduser [accoutn user] root
adduser [account usser] sudo
```