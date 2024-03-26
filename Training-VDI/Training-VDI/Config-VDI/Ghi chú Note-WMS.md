# Ghi chú Note-WMS

![[template-config_port.png]]
![[sms-003.png]]
![[sms-tool.png]]
![[sms-010.png]]
**Gồm các trường hợp:**
- TH1: Dùng ThinC
- TH2: Dùng PC cài ThinOS
- TH3: Dùng PC nhưng không sài VDI
- TH4: Dùng PC vật lý, và hỗ trợ vào VDI
- TH5: Dùng Laptop
- TH6: Cập nhật thông tin chỗ ngồi

### TH1: Dùng ThinC

![[config-thinc-001.png]]
![[config-thinc-002.png]]
![[config-thinc-003.png]]
![[config-thinc-004.png]]
![[config-thinc-005.png]]

### TH2: Dùng PC cài ThinOS
![[config-thinOS-001.png]]
![[config-thinOS-002.png]]
- Barcode: CA-025258
- Check ITC Asset search
- OS: Ubuntu 20 -> ThinOS -> Dùng VDI

### TH3: Dùng PC nhưng không sài VDI
![[config-iprange-001.png]]
![[config-iprange-002.png]]
![[config-move-002.png]]

![[config-move-002.png]]

![[config-move-004.png]]
![[config-move-005.png]]
![[config-iprange-003.png]]

### TH4: Dùng PC vật lý, và hỗ trợ vào VDI

Trường hợp đặc biệt: Dải mạng đặc biệt có thể dùng PC vật lý dự án và VDI 
- VLAN ID 768 - Dải mạng 10.134.68.xx
- VLAN ID 65 - 10.133.65.xx
- VLAN ID 32 - 10.133.32.xx
- Hỗ trợ PC vật lý và dùng vào được VDI
- Port: 
- Để vào được VDI cần chuyển IP của VDI sang dải mạng
- Qua năm phải gia hạn Network Rule mở port
    - Bằng PIM review
    - Check lại ticket đã có yêu cầu
![[config-move-003.png]]
![[config-iprange-VDI-01.png]]
![[config-iprange-VDI-02.png]]

### TH5: Dùng Laptop
![[config-lap-001.png]]
![[config-lap-002.png]]
![[config-lap-003.png]]
![[config-lap-004.png]]
![[config-lap-005.png]]
![[config-lap-006.png]]
Yêu cầu:
- Sử dụng Laptop, không config port mạng vì dùng Wifi 

**Thực hiện:**
- Show VLAN lấy Evidence

### TH6: Cập nhật thông tin chỗ ngồi
![[update_data001.png]]
![[config-update-001.png]]
![[config-update-002.png]]
![[config-update-003.png]]

**Yêu cầu:**
- Update Data, Update Acc

**Thực hiện:**
- Show VLAN lấy Evidence, không config mạng.