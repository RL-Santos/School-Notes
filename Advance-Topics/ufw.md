# What is UFW?
UFW or Uncomplicated firewall, is a cmd tool to simplify firewall management in linux.
This is built on top of `iptables` and it provides user-friendly way to control network traffics

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


## Source
https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands