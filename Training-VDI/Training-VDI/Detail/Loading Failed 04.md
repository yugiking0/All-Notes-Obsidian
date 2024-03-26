The assigned desktop source for this desktop is not currently available. Please try connecting to this desktop again later, or contact your system administrator.

![[Loading_Failed04-image.png|500]]

1. Kiểm tra sơ bộ
- Check IP Client
- Check IP, Account, VDI Name, Trạng thái VDI của Desk Agent

2. Kiểm tra trên Tool:
- Check trạng thái VDI:
	- Maintenance:  
	- Agent Unreachable:
		- Remote vào máy user Kiểm tra xem có phần mềm VMware Horizon Agent và VMware Tools, cài đặt lại agent
		- ping dns name: ko có kết nối -> ==Restart==
		- ping ok  ->  remote vào VDI User -> Chạy lại agent   
![[VPN-image01.png]] 
- Kiểm tra Kiểm tra firewall and vpn
- Kiểm tra vmmem and horizon agent
- Kiểm tra có đang chạy VPN, docker, card ảo
- Remote vào máy user check
- Tắt VPN nếu có

