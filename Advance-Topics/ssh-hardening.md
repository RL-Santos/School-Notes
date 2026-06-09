# SSH
Secure Shell, this ecnrypts data if you want to connect to a remote computer or sever. This is mostly used for Remote command-line access, File Transfers and Tunneling Traffic. This is usually used for tasks like Server Maintenance, Application Deployment and Troubleshooting

Basically, you use SSH to securely access something from far away.

## SSH Authentication
there are 2 types of authentication:
**
- **Password Authentication** - this is the most simple authentication. You enter your username and password then the server checks if its you. The downside is, this is more unsecure because passwords can be guessed or even intercepted

- **SSH Key Authentication** - this involves using 2 keys, ***Public*** and ***Private*** key, to verify if its you using it. How is work basically is, client sends the public key to the server then if its the same as it has then is sends a random string as a challenge. Once the client receives the random strings it uses the private key to solve it then sends it back again. Then the server uses its public key to verify if its correct then if its right it makes the ssh connection.

## Source:
https://youtu.be/P0Fk-K2eZF8