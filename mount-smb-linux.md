### Manually mount the drive
```
sudo mkdir -p /mnt/<mount>
sudo mount -t cifs //<smb_ip>/<shared_mount> /mnt/<mount> -o username=<username>,password=<password>,uid=<uid>,file_mode=0775,dirmode=0775
```
Note: find uid using `id -u`

### Mount the drive using fstab
```
sudo mkdir -p /mnt/<mount>
sudo vim /etc/fstab
```

Then add the line:
```
//<smb_ip>/<shared_mount> /mnt/<mount> cifs username=<username>,password=<password>,uid=<uid>,file_mode=0775,dirmode=0775 0 0
```
