# Basic
---
### 1. Router
#### 1.1 Các quyền - Mode 
- **User Mode**
	- Gần như không có quyền gì cả
	- Dấu nhắc: >
- **Priviledged EXEC Mode - Mode đặc quyền**
	- Để vào Mode bấm: **enable** ( Viết tắt **ena** bấm tab sẽ thể hiện đầy đủ)
	
	![[Pasted image 20231221105743.png | 500]]
```bash
Router > ena
Router > enable
Router # 
```

- Trạng thái đặc quyền full quyền quản trị : Truy cập được tất cả các lệnh ( Command ) và các chức năng ( Freature)
- Không dùng để cấu hình, ==chỉ dùng để xem các cấu hình đang chạy==
- Dấu nhắc: # ( *Router #* )
- Xem các cấu hình đang chạy : # show run

```bash
Router # show run
```
![[Pasted image 20231221105937.png]]

- **Config Mode - Mode cấu hình**
	- Để vào mode bấm: **configure terminal** ( Viết tắt **conf t**)

```bash
Router # conf t
Router # configure terminal
Router (config) # 
```

![[Pasted image 20231221110052.png]]

 - Trạng thái này dùng để cấu hình chính
	- Dấu nhắc: **Router (config) #**
	- Muốn thoát từng cấp Mode thì dùng lệnh **exit** ( Viết tắt là **ex**)
	
![[Pasted image 20231221110444.png]]

- Thoát Mode: Router (config) => Router # => Router >

```bash
Router (config) # ex
Router (config) # exit
Router # ex
Router >
```
#### 1.2 Các lệnh
- Đổi tên thiết bị - Thực hiện ở **Mode Config**
	- Gõ: hostname [Ten_router] ( Viết tắt là host R1)
	
```bash
Router (config) # host R1
Router (config) # hostname R1
R1 (Config) #
```
![[Pasted image 20231221110928.png]]

- **Cấu hình mật khẩu**
	- MK1: Cổng Console
	- MK2: Quyền vào Mode Privileged 
	- MK3: Hỗ trợ  Remote vào thiết bị từ xa

- **MK1: Cấu hình pass vào cổng Console**
	- Câu lệnh: line console 0 ( Viết tắt line con 0)
	- Sẽ vào Mode bên trong của khối lệnh

```bash
R1(config) # line console 0
R1(config-line) # password cisco
R1(config-line) # login
R1(config-line) # exit
```

- Sẽ bị kiểm tra Password khi vào CLI của thiết bị ở **Mode User**

![[Pasted image 20231221112615.png]]

- Thoát lệnh Ctrl Shift 6 -> Đang chạy xử lý
![[Pasted image 20231221112816.png]]

- **MK2: Cấu hình pass vào Mode Privileged **
	- Mode config câu lệnh: **ena pass cisco** hoặc **ena secret cisco**
	- ena pass : Hiển thị clear text khi show run
	- ena secret : Hiển thị encry khi thể hiện - ==Hàm băm 1 chiều, không truy ngược được==
	- Thể hiện: **do show run**

![[Pasted image 20231221113937.png]]

![[Pasted image 20231221114129.png]]

- Muốn bỏ mật khẩu cũ: thêm tiền tố no (90% hủy bỏ câu lệnh đang chạy thì thêm tiền tố này)

```bash
R1(config) # no ena pass
R1(config) # ena sec 123
```

![[Pasted image 20231221114853.png]]

- Nếu gán pass nhiều lần thì sẽ nhận pass cuối cùng được gán

```bash
R1(config) # ena pass 123
R1(config) # ena pass 456
R1(config) # ena pass 789

### Pass sẽ là 789
```

- **MK3: Cấu hình pass Remote**
	- Câu lệnh: line vty 0 15 ( Viết tắt line vty 0 15) Với 0 15 là dải port hỗ trợ
	- Sẽ vào Mode bên trong của khối lệnh

![[Pasted image 20231221113123.png]]


#### 1.3 Mở cổng và đặt IP

![[Pasted image 20231222210659.png]]

- Ở trạng thái R1 (congfig)

```bash
R1(config) # interface gigabitEthernet 0/0
R1(config) # int g0/0
R1(config-if) # no shutdown
R1(config-if) # no sh // Viet tat
R1(config-if) # ip address 192.168.0.1 255.255.255.0
R1(config-if) # description # Port line VLAN 1 #
R1(config-if) # exit
R1(config) # ...
```

#### 1.4 Các câu lệnh khác
**- Mã hóa** khi xem clear text
 
![[Pasted image 20231222202810.png]]

- Ở trạng thái R1 (congfig)

```bash
R1(config) # service password-encryption
R1(config) # ser pass // Viet tat
R1(config) # do show run
```

![[Pasted image 20231222203033.png]]

- **Description:** Mô tả kết nối Port khi mở
- Ở trạng thái R1 (congfig)

```bash
R1(config) # interface gigabitEthernet 0/0
R1(config-if) # de # Port line VLAN 1 #
R1(config-if) # description # Port line VLAN 1 #
```


![[Pasted image 20231222205321.png]]

- Banner Motd : Mô tả banner khi vào thiết bị

banner motd # noi_dung #

```bash
R1(config) # ban motd #Luu y: Nha co cho du#
```

![[Pasted image 20231222211913.png]]
#### 1.9 Tổng hợp

```sh

ena
conf t
host R1
ena pass cisco          // Khai báo mật khẩu Privileged Mode

line cons 0             // Khai báo mật khẩu console -- CLI Mode User
		pass 123
		login
		exit

line vty 0 15            // Khai báo mật khẩu console -- CLI Mode User
		pass 456
		login
		exit
		
ser pass                 // Ma hoa pass khi xem clear text
  
int g0/0                 // Mo port dat IP
		no shut
		ip add 192.168.0.1 255.255.255.0
		desc # Port line VLAN 1 #           // Mo ta port                    
		exit
	
int g0/1
		no shut
		ip add 192.168.10.1 255.255.255.0
		desc # Port line VLAN 2 #
		exit	
	
ban motd #Luu y: Nha co cho du#      // Banner Motd canh bao khi vao thiet bi    

```

![[Pasted image 20231222210631.png]]

![[Pasted image 20231222210858.png]]
