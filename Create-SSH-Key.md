---
tags:
  - linux
---
```bash
cd ~/.ssh

# GitHub key
ssh-keygen -t ed25519 -C "Zorin-Github" -f -f ~/.ssh/id_github


# Start agent and add keys
eval "$(ssh-agent -s)"
ssh-add id_github

# Create ~/.ssh/config
cat <<EOF > ~/.ssh/config
# GitHub
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_github
EOF
```
