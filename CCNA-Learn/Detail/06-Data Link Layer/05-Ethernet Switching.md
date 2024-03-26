**Module Objective**: Explain how Ethernet operates in a switched network.

|**Topic Title**|**Topic Objective**|
|---|---|
|**Ethernet Frame**|Explain how the Ethernet sublayers are related to the frame fields.|
|**Ethernet MAC Address**|Describe the Ethernet MAC address.|
|**The MAC Address Table**|Explain how a switch builds its MAC address table and forwards frames.|
|**Switch Speeds and Forwarding Methods**|Describe switch forwarding methods and port settings available on Layer 2 switch ports.|

![[Pasted image 20240304121705.png]]

## MAC Sublayer

The MAC sublayer is responsible for data encapsulation and accessing the media.

**Data Encapsulation**
IEEE 802.3 data encapsulation includes the following:

- **Ethernet frame** - This is the internal structure of the Ethernet frame.
- **Ethernet Addressing** - The Ethernet frame includes both a source and destination MAC address to deliver the Ethernet frame from Ethernet NIC to Ethernet NIC on the same LAN.
- **Ethernet Error detection** - The Ethernet frame includes a frame check sequence (FCS) trailer used for error detection.

**Accessing the Media**
As shown in the figure, the IEEE 802.3 MAC sublayer includes the specifications for different Ethernet communications standards over various types of media including copper and fiber.

## Ethernet Frame Fields
The minimum Ethernet frame size is 64 bytes and the expected maximum is 1518 bytes. This includes all bytes from the destination MAC address field through the frame check sequence (FCS) field.

![[Pasted image 20240304121938.png]]

### Ethernet Frame Fields Detail

|Field|Description|
|---|---|
|**Preamble** and **Start Frame** Delimiter Fields|The Preamble (7 bytes) and Start Frame Delimiter (SFD), also called the Start of Frame (1 byte), fields are used for synchronization between the sending and receiving devices. These first eight bytes of the frame are used to get the attention of the receiving nodes. Essentially, the first few bytes tell the receivers to get ready to receive a new frame.|
|**Destination MAC** Address Field|This 6-byte field is the identifier for the intended recipient. As you will recall, this address is used by Layer 2 to assist devices in determining if a frame is addressed to them. The address in the frame is compared to the MAC address in the device. If there is a match, the device accepts the frame. Can be a unicast, multicast or broadcast address.|
|**Source MAC** Address Field|This 6-byte field identifies the originating NIC or interface of the frame.|
|Type / Length|This 2-byte field identifies the upper layer protocol encapsulated in the Ethernet frame. Common values are, in hexadecimal, 0x800 for IPv4, 0x86DD for IPv6 and 0x806 for ARP.  <br>**Note**: You may also see this field referred to as EtherType, Type, or Length.|
|Data Field|This field (46 - 1500 bytes) contains the encapsulated data from a higher layer, which is a generic Layer 3 PDU, or more commonly, an IPv4 packet. All frames must be at least 64 bytes long. If a small packet is encapsulated, additional bits called a pad are used to increase the size of the frame to this minimum size.|
|Frame Check Sequence Field|The Frame Check Sequence (FCS) field (4 bytes) is used to detect errors in a frame. It uses a cyclic redundancy check (CRC). The sending device includes the results of a CRC in the FCS field of the frame. The receiving device receives the frame and generates a CRC to look for errors. If the calculations match, no error occurred. Calculations that do not match are an indication that the data has changed; therefore, the frame is dropped. A change in the data could be the result of a disruption of the electrical signals that represent the bits.|

