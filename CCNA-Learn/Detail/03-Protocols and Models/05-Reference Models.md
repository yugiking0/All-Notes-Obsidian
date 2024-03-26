## The Benefits of Using a Layered Model

These are the benefits of using a layered model to describe network protocols and operations:
- Assisting in protocol design because protocols that operate at a specific layer have defined information that they act upon and a defined interface to the layers above and below
- Fostering competition because products from different vendors can work together
- Preventing technology or capability changes in one layer from affecting other layers above and below
- Providing a common language to describe networking functions and capabilities

As shown in the figure, there are two layered models that are used to describe network operations:
- Open System Interconnection (OSI) Reference Model
- TCP/IP Reference Model

![[Pasted image 20240304113041.png]]

## The OSI Reference Model

|**OSI Model Layer**|**Description**|
|------|---|
|**7 - Application**|The application layer contains protocols used for process-to-process communications.|
|**6 - Presentation**|The presentation layer provides for common representation of the data transferred between application layer services.|
|**5 - Session**|The session layer provides services to the presentation layer to organize its dialogue and to manage data exchange.|
|**4 - Transport**|The transport layer defines services to segment, transfer, and reassemble the data for individual communications between the end devices.|
|**3 - Network**|The network layer provides services to exchange the individual pieces of data over the network between identified end devices.|
|**2 - Data Link**|The data link layer protocols describe methods for exchanging data frames between devices over a common media|
|**1 - Physical**|The physical layer protocols describe the mechanical, electrical, functional, and procedural means to activate, maintain, and de-activate physical connections for a bit transmission to and from a network device.|

## The TCP/IP Protocol Model


|**TCP/IP Model Layer**|**Description**|
|---|---|
|**4 - Application**|Represents data to the user, plus encoding and dialog control.|
|**3 - Transport**|Supports communication between various devices across diverse networks.|
|**2 - Internet**|Determines the best path through the network.|
|**1 - Network Access**|Controls the hardware devices and media that make up the network.|

![[Pasted image 20240304113547.png]]

![[Pasted image 20240304113645.png]]
