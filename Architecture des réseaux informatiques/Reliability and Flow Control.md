## TCP: Guaranteed and Ordered Delivery

- resends dropped packets
- number packets
- maintain flow of packets

ISN => initial sequence number

it's incremented at each segment by the number of bytes transmitted. This data byte tracking enables each segment to be uniquely identified and acknowledged.
You can also identify missing segments.

ISN doesn't start at 1 but is a random number to prevent certain type of malicious attacks.

SACK => selective acknowledgment => allows to only retransmit missing data

