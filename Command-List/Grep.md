---
tags:
  - command-list
  - linux
  - macos
---
```sh
  # Find all files containing "error_code"
  grep -r "error_code" /path/to/directory

  # Show filename and line number
  grep -rn "error_code" /path/to/directory

  # Search only Python files
  grep -rn "error_code" /path/to/directory --include="*.py"

  # Case-insensitive
  grep -ri "Error_Code" /path/to/directory
  
  # Only filename
  grep -rl "Error_Code" /path/to/directory
```

