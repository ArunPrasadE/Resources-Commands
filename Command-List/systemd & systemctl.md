---
tags:
  - quick-note
  - linux
  - command-list
---
- `systemd` is the system or process that starts at the booting of the system.
- It can be confirmed by its **PID 0** during the [[ps]] command
- All other process are the child process of `systemd`

# Configuring a process to start at the booting along with systemd

```sh
systemctl [option] [service]
```
- When we want some process to start at the boot (Ex: webservers, db servers etc.,), we can use the above `systemctl` command
- `systemctl` will interact with `systemd` process/daemon and tells it to launch the target process/service
	- `systemctl start apache2` : This will tell `systemd` to launch apache2 during the boot
- We can do five options with `systemctl`:
	- Start
	- Stop
	- Enable
	- Disable
	- Status