---
tags:
  - command-list
  - linux
  - windows
  - macos
---
## Transfer files from Host to remote machine
```sh
scp /<important.txt> <user>@<IP>:/<transferred.txt>
```

## Reverse: Transfer files from remote machine to your host

```sh
scp <user>@<IP>:/<important.txt> /<transferred.txt>
```


| **Variable**                                                | **Value**       |
| ----------------------------------------------------------- | --------------- |
| The IP address of the remote system                         | IP              |
| User on the remote system                                   | user            |
| Name of the file on the local system                        | important.txt   |
| Name that we wish to store the file as on the remote system | transferred.txt |
