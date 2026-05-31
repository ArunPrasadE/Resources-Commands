---
tags:
  - command-list
  - linux
---
```sh
# check current crontab
crontab -l

# Edit cronjobs
crontab -e
```
- If we want to schedule a task to run at regular intervals after the system is booted completely, we can use `cron` process
- This is different from [[systemd & systemctl]]. They are used to start a process during the boot. And `cron` is used to launch process at regular intervals after the boot.
- Crontabs require 6 specific values

| **Value** | **Description**                           |
| --------- | ----------------------------------------- |
| MIN       | What minute to execute at                 |
| HOUR      | What hour to execute at                   |
| DOM       | What day of the month to execute at       |
| MON       | What month of the year to execute at      |
| DOW       | What day of the week to execute at        |
| CMD       | The actual command that will be executed. |
- If we want to backup specific directory at 12hr regular interval, the below command can be used
```sh
0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/
```
- `*` is a specific wildcard used to denote that we don't care about them. In the above example, we dont care about what min, what day, what month and what week the process should run but run every 12 hours.
- For quick crontab command generator, we can use [Crontab generator](https://crontab-generator.org/)