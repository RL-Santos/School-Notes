
#  Transmission Control Protocol or TCP Dump
Tcpdump is a tool for capturing network packets. It basically gives you X-ray vision on network wires

## Packets 
These are bits of data sent to your computer then your computer builds it base on the instruction on it as well

Packet consists of 2 main parts the header and the payload
- The **header** basically has all the info like where it came from, where will it go and how to actually build the data properly
- The **payload** is the deconstructed data which your computer builds base on the header

## Example output of tcpdump (Breakdown)
`21:43:01.102345 IP 192.168.1.5.54321 > 142.250.190.46.443: Flags [P.], seq 1:50, ack 1, win 501, length 49`

- `21:43:01.102345` → The exact timestamp when the packet was caught.

- `192.168.1.5.54321` → The Source IP (192.168.1.5) and the Source Port (54321) that sent the data.

- `'>'` → The direction the traffic is moving.

- `142.250.190.46.443` → The Destination IP and the Destination Port (443, which is standard HTTPS traffic).

- `Flags [P.]` → Network handshake details (in this case, "Pushing" data).

- `length 49` → The size of the payload inside this specific packet (49 bytes).

## Commands:

`sudo tcpdump -D | tcpdump --list-interfaces`
- this lists all interface from tcpdump

`sudo tcpdump --interface any`
- run this if you don't want to choose what interface and just output everything
