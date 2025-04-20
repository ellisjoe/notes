1. Create a new systemd service in `/etc/systemd/system/my-app.service`

```
[Unit]
Description=Health App Server
After=network.target

[Service]
ExecStart=/home/jellis/health-app/health-server
Restart=on-failure
User=jellis
WorkingDirectory=/home/jellis/health-app
Environment=RUST_LOG=info

[Install]
WantedBy=multi-user.target
```

2. Run `sudo systemctl enable my-app`
3. Start it `sudo systemctl start my-app`
4. View status `sudo systemctl status my-app`
5. View logs `journalctl -u my-app -f`
6. Add a new DNS Record to [pi-hole](http://pi-hole.home/admin/dns_records.php)
7. Add an nginx service to pi-hole in `/etc/nginx/sites-enabled/proxy`

```
server {
        listen 80;
        server_name health.home;

        location / {
                proxy_pass http://nuc:9191;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
        }
}
```

8. May need to clear dns caches on Mac

```
sudo dscacheutil -flushcache
sudo killall -HUP mDNSResponder
```
