#### LAN Switch Device Documentation

|Device|Model|Description|Mgt. IP Address|IOS|VTP|
|---|---|---|---|---|---|
|**S1**|Cisco  <br>Catalyst  <br>  <br>WS-  <br>C2960-  <br>24TC-L|Branch-1  <br>  <br>LAN1  <br>switch|192.168.77.2/24|192.168.77.2/24  <br>  <br>Image: C2960-  <br>LANBASEK9-M|Domain: CCNA  <br>  <br>Mode: Server|

|Port|Description|Access|VLAN|Trunk|EtherChannel|Native|Enabled|
|---|---|---|---|---|---|---|---|
|Fa0/1|Port Channel 1 trunk to  <br>S2 Fa0/1|-|-|Yes|Port-Channel  <br>1|99|Yes|
|Fa0/2|Port Channel 1 trunk to  <br>S2 Fa0/2|-|-|Yes|Port-Channel  <br>1|99|Yes|
|Fa0/3|***Not in use***|Yes|666|-|-| |Shut|
|Fa0/4|***Not in use***|Yes|666| | | |Shut|
|Fa0/5|Access port to user|Yes|10|-|-||Yes|
|...||||-|-||-|
|Fa0/24|Access port to user|Yes|20|-|-||Yes|
|Fa0/24| ***Not in use*** |Yes|666|-|-||Shut|
|G0/1|Trunk link to Branch-1|-|-|Yes|-|99|Yes|
|G0/2| ***Not in use***|Yes|666||-||

![[Pasted image 20230919110257.png]]

