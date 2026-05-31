---
tags:
  - command-list
  - linux
---

- We can configure your host as a temporary HTTP file server allowing others to download from your machine
- This is done using python's built in feature `http.server`

```sh
python3 -m http.server
```

- The above command with start a http server in the current directory.
- Then we can use [[wget]] to download the file (If you know the file name) just like downloading from a HTTP website
- But make sure to input the <port-number> given when dowloading
