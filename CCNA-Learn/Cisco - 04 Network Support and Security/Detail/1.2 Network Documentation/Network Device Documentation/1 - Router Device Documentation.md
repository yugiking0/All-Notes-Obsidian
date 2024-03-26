#### Router Device Documentation

The table displays sample network device documentation for two interconnecting routers.

![[Pasted image 20230919105733.png]]

|Device|Model|Description|Location|IOS|License|
|---|---|---|---|---|---|
|**Central**|ISR 4321|Central Edge Router|Building A  <br>  <br>Rm: 137|Cisco IOS XE Software, Version 16.09.04  <br>  <br>flash:isr4300-  <br>universalk9_ias.16.09.04.SPA.bin|ipbasek9  <br>  <br>securityk9|
|**Interface**|**Description**|**IPv4 Address**|**IPv6 Address**|**MAC Address**|**Routing**|
|G0/0/0|Connects to  <br>SVR-1|10.0.0.1/30|2001:db8:acad:1::1/64|a03d.6fe1.e180|OSPF|
|G0/0/1|Connects to  <br>Branch-1|10.1.1.1/30|2001:db8:acad:A001::1/64|a03d.6fe1.e181|OSPFv3|
|G0/1/0|Connects to ISP|209.165.200.226/30|2001:feed:1::2/64|a03d.6fc3.a132|Default|
|S0/1/1|Connects to  <br>Branch-2|10.1.1.2/24|2001:db8:acad:2::1/64|n/a|OSPFv3|
|||||||

|Device|Model|Description|Site|IOS|License|
|---|---|---|---|---|---|
|**Branch-1**|ISR  <br>4221|Branch-2  <br>  <br>Edge Router|Building B  <br>  <br>Rm: 107|Cisco IOS XE Software, Version 16.09.04  <br>  <br>flash:isr4200-universalk9.16.09.04.SPA.bin|ipbasek9  <br>  <br>securityk9|
|**Interface**|**Description**|**IPv4 Address**|**IPv6 Address**|**MAC Address**|**Routing**|
|G0/0/0|Connects to  <br>S1|Router-on-a-stick|Router-on-a-stick|a03d.6fe1.9d90|OSPF|
|G0/0/1|Connects to  <br>Central|10.1.1.2/30|2001:db8:acad:A001::2/64|a03d.6fe1.9d91|OSPF|
