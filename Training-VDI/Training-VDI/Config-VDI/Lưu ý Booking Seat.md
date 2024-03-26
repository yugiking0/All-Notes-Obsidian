### WMS Tool

![[sms-tool.png]]

- Link: https://wms.fsoft.com.vn/
- Khi User thực hiện trên tool sẽ có 1 ticket về ITC. Các thao tác tương ứng với loại ticket tương ứng:
	- Với thao tác return Seat(Trả chổ) thì sẽ có I ticket về ITC là **“[SM][SeatCode][Site] Return Seat“**
	- Với thao tác Booking Seat(book chổ) thì sẽ có I ticket về ITC là **“[SM][SeatCode][Site] Booking Seat“**

- Giao diện một ticket Booking Seat
![[sms-003.png]]

![[sms-004.png]]

![[sms-005.png|400]]

![[sms-009.png]]

![[sms-010.png]]

**Chú ý các mục:**
- (1) **Seatcode**: Cần điền chính xác vị trí Seatcode
- (2) **Account**: Account User sẽ ngồi vị trí này (New Member, TTS chưa có Account thì điền tạm tên PM, Admin => Khi khi có Account thì cần reBooking Seat lại để Update thông tin Account)
- (3) **Purpose**: Phân loại lý do cần config, bao gồm những lựa chọn như sau:
	- Chỗ ngồi của cá nhân
	- Chỗ ngồi dành cho thiết bị/PC/máy test nhỏ
	- Chỗ ngồi dành cho thiết bị cồng kềnh
	- Chỗ ngồi dành cho SVTT/NV mới => *Trường **Barcode** sẽ không bắt buộc nhập*.
	- Chỗ ngồi của laptop => Sẽ không config Port mạng, vì laptop sẽ dùng wifi (*Rule không được cắm laptop vào port mạng và port mạng sẽ được Disabled*)
![[sms-0012.png]]
- (4) **Need to Enable network port**:
	- **Uncheck**: Sẽ không cần config port mạng => Trường hợp Update lại thông tin như Account User
	- **Check**: Cần config port mạng.
- (5) **Barcode**: Thiết bị của user cần kết nối vào port mạng này.
	- Nếu user có 2 thiết bị laptop và PC => ==Cần chọn lựa lại thiết bị phù hợp (Mặc định đôi khi để sẵn mã Laptop)==
	- Laptop : Sẽ không config Port mạng, port này sẽ bị Disable không dùng được.
	- Cần lấy thông tin chính xác mã Barcode kết nối vì sẽ sử dụng thông tin để lấy cấu hình và check 1 số thông tin khác để tăng độ config port mạng.
	- Nếu cột này không tìm thấy Barcode đúng của User => Điền Barcode này ở **Note** (6): Đôi khi chưa đồng bộ nên chưa chọn đúng được Barcode.
	- Note (6) : Ghi chú giúp config Port mạng chính xác hơn, hoặc hiểu rõ hơn yêu cầu cần hỗ trợ port mạng này.

### Note - Ghi chú
- Đúng Barcode thiết bị
	- TH1: ThinC => Dải mạng VDI
	- TH2: PC cài ThinOS => Dải mạng VDI
	- TH3: Chỉ dùng VDI làm việc chính => Dải mạng VDI
	- TH4: PC dự án, không dùng VDI => Cần biết dải mạng dự án
	- TH5: PC chỉ dùng mạng cơ bản => Dải mạng 10.133.172.xx
	- TH6: Update Account, Update Data, không config mạng => Sẽ giữ nguyên và không config mạng.

![[sms-0020.png]]

![[template-config_port.png]]

