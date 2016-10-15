# Telldus

```
§ sudo /etc/init.d/telldusd restart
```

# Aliases

```
pi@pi2:~ $ cat .bash_aliases 
alias ha-logging='sudo journalctl --no-full -o cat -f -u home-assistant@pi'
alias ha-restart='sudo systemctl restart home-assistant@pi'
```

# Home Assistant as Service

```
$ su -c 'cat <<EOF >> /lib/systemd/system/home-assistant@[your user].service
[Unit]
Description=Home Assistant
After=network.target

[Service]
Type=simple
User=%i
ExecStart=/usr/bin/hass

[Install]
WantedBy=multi-user.target
EOF'
```

```
$ sudo systemctl --system daemon-reload
$ sudo systemctl enable home-assistant@[your user]
$ sudo systemctl start home-assistant@[your user]
```

# Home Assistan Logging Output

```
$ sudo journalctl -f -u home-assistant@[your user]
$ sudo journalctl --no-full -o cat -f -u home-assistant@pi
```

# List USB

```
§ lsusb
```
