## About the transport layer

Transport layer => between application and internet layers in TCP/IP model.

Transport layer has no knowledge of the desintation host type, the type of media over which the data travels, its path, link congestion or network size.

- TCP
- UDP

Responsibilities of the transport layer:
- Tracking individual conversations
- Segmenting data and reassembling segments
- add header information
- Identifying the applications
- Conversation multiplexing

Conversation => set of data flowing between a source application and a destination application

transport layer blocks are called segments or datagrams

Adds header information containing binary data organized into several fields. The values in these fields enable various transport layer protocols to perform different functions in managing data communication.

Transport layer ensures that even with multiple applications running on a device all applications receive the correct data (ports)

Transport layer protocols specify how to transfer messages between hosts, and are responsible for managing reliability requirements of a conversation. 

## TCP

IP is not responsible for guaranteeing delivery or determining whether a connection between the sender and receive needs to be established

=> TCP is considered a reliable, full featured transport layer protocol, which ensures that all of the data arrives at the destination. 
=> TCP includes fields which ensure the delivery of the application data. These fields require additional processing by the sending and receiving hosts. 

> [!note]
> TCP divides data into segments

TCP segments are tracked from source to destination. 

TCP provides reliability and flow control using these operations:
- Number and track data segments transmitted to a specific host from a specific application
- Acknowledge received data
- Retransmit any unacknowledged data after a certain amount of time
- Sequence data that might arrive in wrong order
- Send data at an efficient rate that is acceptable by the receiver

TCP must first establish a connection between the sender and the receiver. TCP is a connection-oriented protocol.

## UDP

UDP does not provide reliability and flow control, which means it has less header fields.

UDP datagrams can be processed faster than TCP segments.

UDP is connectionless

UDP is stateless - it does not track information sent or received between client and server

UDP is best-effort - because there is no acknowledgment that the data is received at the destination. 

## Which to choose

Required protocol properties depending on the protocol:

| UDP                              | TCP                              |
| -------------------------------- | -------------------------------- |
| Fast                             | Reliable                         |
| Low overhead                     | Acknowledges data                |
| Does not require acknowledgments | Resends lost data                |
| Does not resend lost data        | Delivers data in sequenced order |
| Delivers data as it arrives      |                                  |


