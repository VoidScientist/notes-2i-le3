Used to manage multiple, simultaneous conversations.

Source port number is associated with the originating application on the local host whereas the destination port number is associated with the destination application on the remote host.

## Socket Pairs

192.168.0.3:8080 => example of a socket

it is a unique IP - Port pair.

## Port Number Groups

| Port Group              | Number Range   | Description                                                                                                                                                                                                            |
| ----------------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Well-Known Ports        | 0 to 1023      | - reserved for common or popular services and applications.<br><br>- defined well-known ports for common server applications enables clients to easily identify the associated service requires                        |
| Registered Ports        | 1024 to 49151  | - Assigned by IANA to a requesting entity<br><br>- Individual applications installed by user<br><br>- Cisco has registered port 1812 for RADIUS server auth process                                                    |
| Private / Dynamic Ports | 49152 to 65535 | - These ports are also known as ephemeral ports<br><br>- The client's OS usually assign port numbers dynamically when a connection is initiated.<br><br>- Used to identify the client application during communication |

