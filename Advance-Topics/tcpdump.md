
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

- `Flags [P.]` → Network handshake details. This tells what the packet wants to do or did.

- `seq 1:50` → The sequence number, this gives you what part of the flow this it. In this case if the flow is 500 bytes long, this contains the 1-50 bytes 

- `ack 1` → The acknowledgement number, this just means it acknowledges that I received the sequence 1-50 send in the next one.

- `win 501` → The window size, this tells the other computer it that it only has this much space left and wait till I delete something if its over the said capacity.

- `length 49` → The size of the payload inside this specific packet (49 bytes).

## TCP Flag Common Types
These are types of network handshakes that you can see in the example above

| Value | Type | Description       |
|-------|------|-------------------|
| S     | SYN  | Connection Start  |
| F     | FIN  | Connection Finish |
| P     | PUSH | Data push         |
| R     | RST  | Connection reset  |
| .     | ACK  | Acknowledgment    |

It is possible to see multiple flags in an output like [S.] that just means its combination of both meaning its a SYN-ACK packet

## Commands:

`sudo tcpdump -D | tcpdump --list-interfaces`
- this lists all interface from tcpdump

`sudo tcpdump --i any`
- run this if you don't want to choose what interface and just output everything

`sudo tcpdump -i any -c5`
- -c 5 means only the first 5 packets that are captured will be the only thing outputted

`sudo tcpdump -i any -c5 -n`
- this gives the raw name catched by system and not translate it to readable human language

`sudo tcpdump -i any -c5 -nn`
- this gives the raw name and the raw port catched by the system and not translate it to readable human language

`sudo tcpdump -i any -c10 -nn -A port 80`
- this prints the contents of the output into a ASCII

`sudo tcpdump -i any -c10 -nn -X port 80`
- this prints the contents of the output into a Hex

`sudo tcpdump -i any -c10 -nn -w webserver.pcap port 80`
- -w means it will write it in the specified file after it
- '.pcap' means packet capture and the terminal writes it in binary so you can't open it in text editor

`tcpdump -nn -r webserver.pcap src 54.204.39.132`
- this is how you read the a '.pcap' file and filters it in that specific source

---

### Filters
You can combine some of these into one request

`sudo tcpdump -i any -c5 icmp`
- this filters base on protocols which captures and displays only ICMP packets

`sudo tcpdump -i any -c5 -nn host 54.204.39.132`
- this filters base on host which captures and displays only packets to and from host 54.204.39.132

`sudo tcpdump -i any -c5 -nn port 80`
- this filters base on port which captures related to a web (HTTP) service

`sudo tcpdump -i any -c5 -nn src 192.168.122.98`
- this filters base on source which capture packets from host 192.168.122.98

`sudo tcpdump -i any -c5 -nn dst 192.168.122.98`
- this filters base on destination IP or hostname which also capture packets from host 192.168.122.98

---






Source:
https://www.markdownguide.org/basic-syntax/#code
