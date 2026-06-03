# NMAP or Network Mapper
- used for network discovery and security auditing
- Host = The Building
- IP   = The Building Address
- Port = The Apartment Numbers

Commands: 
### nmap -sP 192.168.1.1/24
  - Scans every device connected to my router base on the subnet

### nmap scanme.nmap.org
  - this doesn't work for me but this in theory scans the "scanme.nmap.org" for all 1000 well-known ports
  - I did "nmap -6 scanme.nmap.org" to use IPv6 because that's what my terminal told me to do and it works just a lot more time consuming
### sudo nmap -6 -sS scanme.nmap.org
  - this doesn't have sudo in the website but I put some because my terminal said it needs root permission
  - -sS basically does a stealth scan not sure but this scans a lot faster than the one without -sS
### nmap -6 -sV scanme.nmap.org
  - this gives me the web server software type like apache and the operating system where the server is being ran like ubuntu
### nmap -6 -A scanme.nmap.org
  - this makes the scan more aggressive, it gives much better info about the website you put but the website can detect your scan more easily

### nmap 192.164.1.*
  - this scans multiple hosts at the same time, you use the '*' if you want to scan every subnet. PS, scanning all subnets takes so much time XD
### nmap 192.164.1.1 192.164.0.2
  - you put every ip next to each other if you want to scan multiple specific hosts
### nmap 192.164.0.1,2,3,4
  - use comma ',' in between the address if you don't want to type the whole domain for each hosts (only works if that part is the only difference)
### nmap 192.164.0.0–255
  - use hypen '-' in between the adresss if you want it to scan in that range range

### nmap -p 973 192.168.0.1
  - this doesn't work for me but says on the website that it should check the specific port of the specific ip address
### nmap -p T:7777,U:973 192.168.0.1
  - this means it will scan port 7777 using TCP and the port 973 using UDP from the specific ip address
### nmap -p 76–973 192.164.0.1
  - use hypen '-' in between the specific ports to scan in that range
### nmap --top-ports 10 scanme.nmap.org
  - this scans only the top 10 well-known ports in a website, this I think is more quiet than scanning all ports because you only send 10 packets

### nmap -iL /input_ips.txt
  - this scans but instead of specifying the ip directly in the terminal, this reads the file you put and it uses that to scan all ip in it.

### nmap -v scanme.nmap.org
  - this scans the website but will do a verbose scans which just means instead of dumping everything once its done, it will output what it discover immediately 
### nmap -oN output.txt scanme.nmap.org
  - this scans the website but instead of printing what it got in the terminal it outputs everything in the specific file you put, if there is no file named like that it will make one
### nmap -oX output.xml scanme.nmap.org
  - this scans too but instead of using txt file it will print it in a xml file
### nmap -oA output scanme.nmap.org
  - this scans just like the other one but instead of specifying a file type it will put the output to multiple file types

### nmap -h or nmap --help
  - there are many commands so just incase this outputs all possible things I can do 



Source:
https://www.freecodecamp.org/news/what-is-nmap-and-how-to-use-it-a-tutorial-for-the-greatest-scanning-tool-of-all-time/
