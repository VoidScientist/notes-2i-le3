## Features

- Data is reconstructed in the order that it is received
- Any segments that are lost are not resent
- No session establishment
- The sending is not informed about resource availability

(more information search RFC)

## Header

8 bytes

- Source Port
- Destination Port
- Length
- Checksum

(all 16 bits or 2 bytes)

## Header Fields

| UDP Header Field | Description                                             |
| ---------------- | ------------------------------------------------------- |
| Source Port      | What it means                                           |
| Destination Port | What it means                                           |
| Length           | Length of the UDP datagram header                       |
| Checksum         | Used for error checking of the datagram header and data |

## Applications that use UDP

- Live video and multimedia applications
- Simple request and reply applications
- Applications that handle reliability themselves

DHCP
DNS
SNMP
TFTP
VoIP

