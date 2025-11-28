## Handshake

SYN (SEQ = 100, CTL = SYN) => whatever that means

ACK (SEQ = 300 ACK = 101, CTL = SYN, ACK) => whatever that means

Handshake phase go 
- client send SYN
- server answers SYN and ACK
- client answers ACK

## Termination

- A sends FIN
- B sends ACK
- B sends FIN
- A sends ACK

## Three Way handshake

TCP is full duplex where each connection represents two one way communication sessions.

Functions of three way handshake:
- It establishes that the destination device is present on the network
- It verifies that the destination device has an active service and is accepting requests on the destination port number that the initiating client intends to use.
- It informs the destination device that the source client intends to establish a communication session on that port number

After the communication is completed the sessions are closed, and the connection is terminated. The connection and session mechanisms enable TCP reliability functions.

## Control Bits

Six flags are:
- URG
- ACK
- PSH
- RST
- SYN
- FIN

