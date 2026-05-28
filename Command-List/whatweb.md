---
tags:
  - command-list
  - cybersecurity
  - info-gather
---
```sh
whatweb <x.x.x.x-x.x.x.y> --aggression <1/2/3> -v --no-errors --log-verbose=<file-name>
```

- Used to analyse webpages (HTTP(S))
- Or you can use it to scan a range of IP's (example: your LAN) to identify any open HTTP(S) ports and its details
-  `aggression`
    - Lv1 : Stealthy - sends only 1 HTTP request and gather data
    - Lv2: Aggressive - If a level 1 plugin is matched, additional requests will be made.
    - Lv3: Heavy - Sends multiple HTTP requests to gather data
- `-v`
    - Verbose output for clean readable output
- `--no-errors`
    - Skips displaying error or unidentifiable IP addresses
- `--log-verbose`
    - Saves the file in verbose output format
