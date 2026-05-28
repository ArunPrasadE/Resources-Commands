---
tags:
  - command-list
  - cybersecurity
  - scanning
---
```sh
nmap <IP/IP-range/domain-name>
```

> `-sS` : Maps the target by **only sending the TCP SYN packets** of the 3 way handshake. Does not initiates the full TCP connection. (Requires `sudo` priv)
> `-sT`: Maps the target by **establishing complete TCP connection**. Leaves traces on the target easy to detect. (Does not require `sudo` priv)
> `-sU`: Maps the target by sending **UDP** packets. (Requires `sudo` priv)
> `-O` : Used to identify the **OS type** and **OS version** of the target device
> `-sV` : Used to identify the **version** of the **services** running on the target device
> `-A` : **Aggressive** scan. Includes `-O` and `-sV` and much more by default. **DO NOT** try on targets without permission
> `-p <port1,port2> or <port1-port100>` : Scans only the specified port. (default: 1000 ports)
> `-F` : Scans **top 100 ports**. Does a quick scan.


- Used to check open ports in a specific IP address or a range of IP address (Subnet)
- By default it scans the 1000 most used ports. But it can be specifically told to scan more ports.
- `nmap` default scan type is `-sn`  (No port scan) similar to `netdiscover` which uses ICMP. (Might be blocked by Apple devices)
- To know more about the scan types. Check `man nmap`
- You can also check [[Nmap-Cheatsheet.pdf]]

## Other useful flags

> `-S <IP> -Pn` : Spoofs the IP address with the given IP address.
> `-g <port>` : Specifies the source port to send the scan packets to
> `-e <int>` : Specifies the source interface
> `-sF` : Fin scan. Used if `sS` is blocked by a firewall by just sending a [[TCP-FIN-Scan]] packet without any additional flags