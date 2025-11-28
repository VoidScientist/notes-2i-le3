## Features

- Session establishment *(connection-oriented, negotiate the amount of traffic that can be forwarded at a given time)*
- Reliable Delivery *(ensures sent segments are received)*
- Same-Order Delivery *(ensures proper reassembling of segments)*
- Flow Control *(Request reduction of data flow)*

(Search RFC 793 for more informations)

## Header

TCP is a stateful protocol, which means it keeps track of the state of the communication session.

TCP segments adds 20 bytes of overhead when encapsulating the application layer.

Source Port (16)
Destination Port (16)
Sequence Number (32) 
Acknowledgment Number (32)
Header Length (4)
Reserved (6)
Control Bits (6)
Window (16)
Checksum (16)
Urgent (16)
Options (0 or 32\*3 if any)

## Header Fields

| TCP Header Fields     | Description                                                          |
| --------------------- | -------------------------------------------------------------------- |
| Source Port           | What it means                                                        |
| Destination Port      | What it means                                                        |
| Sequence Number       | Used for data reassembly                                             |
| Acknowledgment Number | Indicate that data has been received and the next byte expected      |
| Header Length         | "data offset" indicates the length of the TCP segment header         |
| Reserved              | Reserved for future use                                              |
| Control Bits          | Bit codes which indicate the purpose and function of the TCP segment |
| Window Size           | Number of bytes that can be accepted at one time                     |
| Checksum              | Used for error checking                                              |
| Urgent                | Used to indicate if the contained data is urgent                     |

## Applications that use TCP

SMTP
FTP
HTTP
SSH

