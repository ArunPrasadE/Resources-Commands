---
tags:
  - command-list
  - linux
  - macos
---
```sh
  # Case-insensitive (matches apple, APPLE, Apple)
  find /path/to/directory -iname "*Apple*"

  # Only files, not directories
  find /path/to/directory -type f -name "*Apple*"

  # Only directories
  find /path/to/directory -type d -name "*Apple*"
```

