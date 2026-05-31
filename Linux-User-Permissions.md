---
tags:
  - linux
---
- in linux each file can be granularity set user permissions.
- User permission for each file can be seen from `ls -l` output. 
- Three types of permission
	- Read `r`
	- Write `w`
	- Execute `x`
- Written in format such as `rwrwxrwx`

| Section | Applies to |
| ------- | ---------- |
| First 3 | Owner      |
| Next 3  | Group      |
| Last 3  | Others     |

## Numerical representation
- The above permissions can also be written numberically
	- Read - 4
	- Write - 2
	- Execute - 1

| Group  | Permissions | Calculation | Value |
| ------ | ----------- | ----------- | ----- |
| Owner  | `rwx`       | 4 + 2 + 1   | 7     |
| Group  | `rwx`       | 4 + 2 + 1   | 7     |
| Others | `rwx`       | 4 + 2 + 1   | 7     |

So `rwxrwxrwx` = `777`
- Numerical representation is important because many linux commands use numerical values 
	- `chmode 755 file`
	- `chmod 750 file.txt`
### Common examples

| Symbolic    | Numeric | Meaning                                              |
| ----------- | ------- | ---------------------------------------------------- |
| `rwxr-xr-x` | 755     | Owner can do everything, others can read and execute |
| `rw-r--r--` | 644     | Owner can read/write, others can only read           |
| `rwx------` | 700     | Only the owner has access                            |
