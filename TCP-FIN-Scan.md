---
tags:
  - cybersecurity
---
- TCP Fin scan is a type of *Stealth scan* used to identify open ports by sending a TCP packet with only a FIN (Finish).
- It bypasses the standard 3 way handshake
- This type of scan do not work with Windows devices and some older Cisco devices. They send `RST` packet regardless if the port is open or not
## Types of results
| **Target Response**  | **Nmap Port State** | **Meaning**                                                 |
| -------------------- | ------------------- | ----------------------------------------------------------- |
| **No Response**      | `open               | filtered`                                                   |
| **RST Packet**       | `closed`            | The port is definitely closed.                              |
| **ICMP Unreachable** | `filtered`          | An intermediate device (firewall/router) blocked the probe. |
