# SS and Netstat
**Netstat** is short for network statistics, this is used to display network connections and more.

**ss** is short for socket statistics, this is basically a more modern and mouch better netstat because it gives more option and gives faster response.

## Example of Outputs
### Netstat
| Proto | Recv-Q | Send-Q | Local Address:Port | Foreign Address     | State      |
|-------|--------|--------|--------------------|---------------------|------------|
| tcp   |      0 |      0 | 192.168.1.50:22    | 192.168.1.112:53432 | ESTABLISHED|

- **Proto** - determines if its TCP or UDP  
- **Recv-Q** - Receive Queue,   
- **Send-Q** - Send Queue,   
- **Local Address** - this is the machine where socket came
- **Foreign Address** - this is where socket is going
- **State** - this will be blank for UDPs, but this shows what happened or happening

### SS
| Netid | State   | Recv-Q | Send-Q | Local Address:Port | Peer Address:Port   |
|-------|---------|--------|--------|--------------------|---------------------|
| tcp   | ESTAB   |      0 |      0 | 192.168.1.50:22    | 192.168.1.112:53432 |

## Netstat and SS Stats
| Name        | Description                                                       |
|-------------|-------------------------------------------------------------------|
| LISTEN      | Waiting for an incoming connection request.                       |
| SYN_SENT    | Local side sent a connection request (SYN) and is waiting for a reply |
| SYN_RECV    | Local side received a connection request and is waiting for final confirmation |
| ESTABLISHED | The connection is fully open and actively transferring data       |
| FIN_WAIT_1  | Local side initiated a close and is waiting for the remote side's reply |
| FIN_WAIT_2  | Local side acknowledged the remote close, waiting for the remote side to finish up |
| CLOSING     | Both sides tried to close at the exact same time                  |
| TIME_WAIT   | Connection is closed, but waiting briefly to catch and discard any lingering, delayed network packets |
| CLOSE_WAIT  | Remote side initiated a close; local side is waiting for the local application to release the connection |
| LAST_ACK    | Local side finally closed its end and is waiting for the final acknowledgment from the remote side |
| CLOSED      | The connection is completely dead and all resources are released  |


## Commands:
I didn't specify if the command is netstat or ss because its almost the same.  

`-t` - this displays every TCP connections  
`-u` - this displays every UDP connections  
`-l` - this displays every listening sockets  
`-n` - this displays all addresses and ports in numerical form

## Source  
https://wafaicloud.com/blog/exploring-network-connections-with-netstat-and-ss-in-linux/