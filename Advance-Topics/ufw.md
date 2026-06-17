# What is UFW?
UFW or Uncomplicated firewall, is a cmd tool to simplify firewall management in linux.
This is built on top of `iptables` and it provides user-friendly way to control network traffics

## What is the difference between UFW and firewalld?
UFW is the default firewall manager on ubuntu-based systems, while firewalld is used on other linux distributions espescially Red Hat-based systems.

firewalld supports both runtime and permanent rules. Runtime rules happens immediately without restarting the device whilst permanent rules persist even if you reboot. 

|       Feature       |                       UFW                       |                 firewalld                |
|:-------------------:|:-----------------------------------------------:|:----------------------------------------:|
| Default on          | Ubuntu, Debian                                  | RHEL, CentOS, Fedora                     |
| Configuration style | Static, rule-based                              | Dynamic, zone-based                      |
| Zones               | Not supported                                   | Fully supported                          |
| Rule types          | Persistent                                      | Runtime and permanent                    |
| GUI support         | GUFW (Graphical Uncomplicated Firewall) (basic) | firewall-config, Cockpit (advanced)      |
| Syntax simplicity   | Simple, human-readable CLI                      | More flexible but more complex           |
| Backend             | iptables or nftables (indirectly)               | iptables or nftables                     |
| Use case focus      | Basic host firewalling                          | Multi-interface, multi-zone environments |

## Key Takeaways

- **UFW Simplifies Firewall Management**: UFW is a user-friendly interface for managing iptables, designed to simplify firewall configuration on Ubuntu-based systems.

- **Default Policies Are Secure by Design**: By default, UFW denies all incoming connections and allows all outgoing connections, creating a secure baseline for most servers.

- **Always Allow SSH Before Enabling UFW**: If you’re connected via SSH, enable SSH access with sudo ufw allow OpenSSH before activating UFW to avoid losing remote access.

- **Use Application Profiles When Available**: UFW integrates with application profiles (e.g., Nginx Full, OpenSSH), allowing easier rule creation without specifying port numbers manually.

- **Support for IP-Based Rules**: You can allow or block traffic from specific IP addresses or subnets using simple commands like ufw allow from IP or ufw deny from subnet.

- **Interface-Specific Rules Offer Granular Control**: UFW allows rule targeting per network interface, which is useful for multi-interface systems and virtualized environments.

- **UFW Integrates with Both IPv4 and IPv6**: Rules apply to both IP versions unless explicitly disabled. You’ll see (v6) entries in the status output for IPv6 rules.

- **Docker Can Conflict with UFW**: Docker modifies iptables directly, potentially bypassing UFW rules unless additional configuration is applied.

- **UFW Rules Can Be Reset or Deleted Easily**: Use ufw reset to wipe all rules or ufw delete to remove specific ones, including by rule number for precision.

- **Best Practices Enhance Security and Maintainability**: The guide emphasizes clear practices: setting default policies early, backing up rule sets, using logging, and avoiding use of firewalld alongside UFW. <$>

## Commands
`sudo ufw status` - this shows you if your firewall is active or not  
`sudo ufw enable` - this enables the firewall and will be enabled on startup  
`sudo ufw status verbose` - this would give you more information about ufw status
- `sudo ufw default deny incoming` this denies all incoming connections (used in most servers)
- `sudo ufw default allow outgoing` this allows all outgoing connection (default)
- `sudo ufw default deny routed` this denies all traffics (used in routers and gateways)

`sudo ufw disable` - this disables the firewall and the ufw  
`sudo iptables -L` - this is used to see if UFW is managing my iptable rules  
`sudo ufw deny from <IP Address>` - this blocks the specific IP Address you want and if you do the status command it will now show there that, that specific ip is not blocked  
`sudo ufw deny from <IP Address>/24` - this would block all IP addresses in the example subnet  
`sudo ufw deny in on eth0 from <IP Address>` - this would block all incoming connection to a specific IP Address to a specific network interface  
`sudo ufw allow from <IP Address>` - this allows all network connections that originate from that specific IP Address  
`sudo ufw allow in on eth0 from <IP Address>` - this would allow all incoming connection from a specific IP Address to a specific network interface  
`sudo ufw delete allow from <IP Address>` - this would delete the allow rule you give to that specific IP Address, you can also replace it to deny to delete that rule too  
`sudo ufw status numbered` - this would list all rules with corresponding rule ID and IP its from  
`sudo ufw delete <rule number>` - this would delete that specific rule you can see in the previous command  
`sudo ufw app list` - this would list all available application profiles  
`sudo ufw allow "OpenSSH"` - this would enable application profile which is in this case OpenSSH, this would allow all incoming connections on the defalut SSH port
`sudo ufw allow OpenSSH` - this would enable the OpenSSH UFW application profile to allow all connections to the default SSH port  
`sudo ufw allow from <IP Address> proto tcp to any port 22` - this would allow all incoming connection from a specific IP Address or subnet to port 22 which is SSH's default port  
`sudo ufw allow from <IP Address> to any port 873` -  this would allow only rsync connections coming from the specific IP Address  
`sudo ufw app list | grep Nginx` - this would identify which Nginx profiles are available  
`sudo ufw allow "Nginx Full"` - this would allow HTTP and HTTPS traffic on the server for nginx  
`sudo ufw app list | grep Apache` - this would identify which Apache profiles are available  
`sudo ufw allow "Apache Full"` - this would allow HTTP and HTTP traffic on the server for apache  
`sudo ufw allow http` - this would allow all incoming HTTP requests  
- `sudo ufw allow 80` - this is the same as the command above  

`sudo ufw allow https` - this would allow all incoming HTTPS requests  
- `sudo ufw allow 443` - this is the same as the command above

`sudo ufw allow proto tcp from any to any port 80,443` - this would allow all incoming HTTP and HTTPS connections  
`sudo ufw allow from <IP Address> to any port 3306` - this would allow MySQL connections from specific IP Address or subnet  
`sudo ufw allow from <IP Address> to any port 5432` - this would allow PostgreSQL connections from specific IP Address or subnet  
`sudo ufw reset` - this would reset ufw back to default configuration  





## Source
https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands