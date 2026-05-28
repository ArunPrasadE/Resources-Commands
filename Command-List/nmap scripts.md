---
tags:
  - command-list
  - cybersecurity
---
```sh
nmap —-script <script-name or script-category> <IP/Domain>
```
- Scripts are a set of nmap exploit commands that are grouped into below categories.
- They can be either run as a grouped category or as a single script.
- Individual scripts are located at `/usr/share/nmap/scripts`
- Details of the script groups are given in [NMAP official website](https://nmap.org/book/nse-usage.html)
- Currently defined categories are `auth`, `broadcast`, `brute`, `default`. `discovery`, `dos`, `exploit`, `external`, `fuzzer`, `intrusive`, `malware`, `safe`, `version`, and `vuln`

