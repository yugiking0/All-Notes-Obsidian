# LỖI COULDN’T CONNECT TO SERVER


![[could_not_connect_server-image.png|500]]

Thường xuất hiện khi User dùng thiết bị PC/Laptop cài App VMware Horizion Client và khai báo sai Domain Server VDI

1. Kiểm tra Domain Server đã đúng domain sau:   
- **Dùng cho Lan tại công ty**
	- vdi-dn.fsoft.com.vn
- **Dùng cho wifi và kết nối tại nhà**
	- Vdi-dn01.fsfot.com.vn
	- Vdi-dn02.fsfot.com.vn
2. Đối với Lan tại công ty:
- Cần kiểm tra ip có thuộc dãy mạng để dùng VDI hay không
- Cụ thể dãy mạng ThinC 10.134.96.0/21
3. Thao tác:
- Lấy CI Name thiết bị
- Kiểm tra thiết bị đã nhập IP chưa
- Kiểm tra IP hiện tại của thiết bị có nằm ở dải IP hỗ trợ VDI không?
- Check lại VLAN ID Seatcode và chuyển để dải mạng phù hợp có hỗ trợ VDI
- ...