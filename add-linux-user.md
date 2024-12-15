```
# -m creates the home folder
sudo useradd -m <username>

# Optionally add them as sudoer
sudo useradd <username> sudo

# Change default shell to `bash`
sudo chsh -s /bin/bash <username>
```
