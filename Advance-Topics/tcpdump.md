
# TCP Dump or Transmission Control Protocol

- Tcpdump is a tool for capturing network packets. It basically gives you X-ray vision on network wires
- Packets are bits of data sent to your computer then your computer builds it base on the instruction on it as well
- Packet consists of 2 main parts the header and the payload
- The header basically has all the info like where it came from, where will it go and how to actually build the data properly
- The payload is the deconstructed data which your computer builds base on the header

- 21:43:01.102345 IP 192.168.1.5.54321 > 142.250.190.46.443: Flags [P.], seq 1:50, ack 1, win 501, length 49

## Commands:

`sudo tcpdump -D | tcpdump --list-interfaces`
- this lists all interface from tcpdump
