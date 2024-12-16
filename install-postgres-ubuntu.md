```
sudo apt update && sudo apt upgrade -y
sudo apt install postgresql

# Check things are running
sudo systemctl status postgresql

sudo su postgres
createuser $USER -P --interactive
```
