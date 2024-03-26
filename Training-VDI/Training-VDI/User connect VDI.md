**ĐIỀU KIỆN CẦN VÀ ĐỦ ĐỂ MỘT USER KẾT NỐI ĐƯỢC TỚI VDI**

![[user_connect_VDI-image.png]]

**Giải Thích:**
- User ==cần có account== để đăng nhập vào VDI
- User dùng các thiết bị ThinC, ThinOS, PC vật lý, Laptop để connect vào Server Horizon
- Các thiết bị trên cần được kết nối vào Vlan 796 hoặc các Vlan đã được mở port ==22443== để có thể kết nối được đến ==Server Horizon==
- User connect vào Server Horizon qua các domain
	- Vdi-dn.fsoft.com.vn             ==(khi dùng qua Lan)==
	- Vdi-dn01.fsoft.com.vn           (khi dùng wifi)
	- Vdi-dn02.fsoft.com.vn           (khi dùng wifi)
	- *vdi-dnuat.fsoft.com.vn          (Dự phòng LAN-UAT giảm tải cho IT)*

- Tiếp đến nhập account đã được cấp vào sau khi đã add domain thành thông
- Vào Pool VDI
- Kết nối thành công đến VDI

![[restart_vdi.png]]

![[restart_vdi2.png]]
