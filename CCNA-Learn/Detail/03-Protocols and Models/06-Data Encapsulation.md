## Segmenting Messages
This leads to segmenting messages having two primary benefits:
- **Increases speed** - Because a large data stream is segmented into packets, large amounts of data can be sent over the network without tying up a communications link. This allows many different conversations to be interleaved on the network called multiplexing.
- **Increases efficiency** -If a single segment is fails to reach its destination due to a failure in the network or network congestion, only that segment needs to be retransmitted instead of resending the entire data stream.

## Protocol Data Units
![[Pasted image 20240304114100.png]]
![[Pasted image 20240304114118.png]]
==***The Layer 2, data link protocol is only used to deliver the packet from NIC-to-NIC on the same network. The router removes the Layer 2 information as it is received on one NIC and adds new data link information before forwarding out the exit NIC on its way towards the final destination.***==

The IP packet is encapsulated in a data link frame that contains the following data link information:
- **Source data link address** - The physical address of the NIC that is sending the data link frame.
- **Destination data link address** - The physical address of the NIC that is receiving the data link frame. This address is either the next hop router or the address of the final destination device.



