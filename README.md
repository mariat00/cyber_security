# Hack the box - Meow
This is my first machine

## Environment
- Operating System: Fedora (Linux)
  
- VPN: Openvpn
  
- Tool: nmap
## 1. Connecting to Hack The Box  VPN
I connected to the Hack The Box VPN using OpenVPN

<img width="443" height="503" alt="Screenshot From 2026-09-23 13-24-58" src="https://github.com/user-attachments/assets/7f9c4691-2845-480b-84ff-0c3120cf5d28" />

Click the Start Machine button to obtain the IP address


<img width="688" height="163" alt="Screenshot From 2026-09-23 13-31-41" src="https://github.com/user-attachments/assets/efc1c668-13ef-4a3b-9353-816c180438d9" />
<br>
<br>
<img width="1366" height="343" alt="Screenshot From 2026-09-23 12-18-47" src="https://github.com/user-attachments/assets/546b44c8-1707-47c7-a1f8-4b92e2e95d42" />
<br>
<br>

## 2. Connectivity
We open another terminal and check connectivity using the ping command
<br>
<br>
<img width="890" height="152" alt="Screenshot From 2026-09-23 01-11-44" src="https://github.com/user-attachments/assets/bee7925d-1563-41da-b559-72001c5e0570" />
<br>
<br>
At this point, I encountered an issue caused by having multiple VPN connections active simultaneously. When checking my network interfaces using `ip addr` or `ifconfig`, I found several VPN interfaces (`tun0`, `tun1`, `tun2`, and `tun3`).

To resolve this, I terminated all active OpenVPN processes using `sudo pkill openvpn` and then reconnected to the VPN.

Finally, to verify the correct VPN connection and confirm the assigned IP address, I used the following command:
`ip route get <HTB_IP>`
<br>
<br>
<img width="655" height="104" alt="Screenshot From 2026-09-23 12-47-00" src="https://github.com/user-attachments/assets/86294584-be49-481b-80c7-edd7a18dd173" />
<br>
<br>
We can now check its connectivity using the `ping` command.
<br>
<br>
<img width="703" height="165" alt="Screenshot From 2026-09-23 12-52-48" src="https://github.com/user-attachments/assets/5285358f-0928-4c23-ae6b-49911d97dfc7" />
<br>
<br>
## 3. Enumeration
We will perform a basic Nmap scan, which will scan the 1000 most common ports
<br>
<br>
<img width="703" height="189" alt="Screenshot From 2026-09-23 12-53-34" src="https://github.com/user-attachments/assets/ca05bfe1-14e4-442b-9617-b3200c51c4ab" />
<br>
<br>

## 4. Acces
The scan showed that port 23/tcp was open and associated with the Telnet service
This indicated that Telnet was available as a potential method of remote access
I used: `telnet + IP + port 23`
<br>
<br>
<img width="716" height="373" alt="Screenshot From 2026-09-23 12-54-48" src="https://github.com/user-attachments/assets/257c2ee8-0210-4780-8c25-1ae1eac3f418" />
<br>
I attempted to log in using common usernames such as `user, admin, and root`
<br>
Finally, I found the flag.
<br>
<br>
<img width="655" height="128" alt="Screenshot From 2026-09-23 01-41-51" src="https://github.com/user-attachments/assets/a3a0ef09-346b-4fe9-acf4-9e14cf105e00" />
