---
tags:
  - linux
  - command-list
---
- Processes and programs running on your linux machine have their own unique Process ID `PID`
- They can be viewed using the command `ps`
- `ps` is used to only view processes related to the local user.
- To check processes related to all users, we can use `ps aux`
- To view realtime process and their cpu usage, we can use `top` 
- To check the processes that start at the boot of the system, check [[systemd & systemctl]]

## Kill a process
- We can kill process using their PID
	- `kill <PID>`
- We can also specify signals when we kill PID
	- *SIGTERM* - Kill the process, but allow it to do some cleanup tasks beforehand
	- *SIGKILL* - Kill the process - doesn't do any cleanup after the fact
	- *SIGSTOP* - Stop/suspend a process
