# Access Denied

![[access_deny-image.png|500]]

- Hỏi lại User đăng nhập đến bước nào xuất hiện báo lỗi
	- Bước 1: Nhập pass 
	- Bước 2: Nhập OTP

1. Không nhập đúng Pass or OTP
	- Kiểm tra account bằng cách đăng nhập vào ess
	- Vẫn vào được ESS nhưng vẫn lỗi
		- Thử nhập trên 1 thiết bị VDI khác/Laptop
		- Đổi Pass lại vì có thể chứa ký tự đặc biệt trong Pass mà OS ThinC hiện tại chưa hỗ trợ => Upgrade OS lên phiên bản mới nhất, change pass khác.

2. Nếu đã login được tới bước OTP thì chỉ cần kiểm tra QR Code
	- Kiểm tra đúng QR code của VDI (user đôi khi nhầm QRCode MFA)
	- Kiểm tra thời gian trên máy và thiết bị xác thực: 30 giây