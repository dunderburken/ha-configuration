# Telldus

```
apt list --installed | grep telldus

sudo nano /etc/apt/sources.list

deb http://download.telldus.com/debian/ stable main

sudo apt-get update

sudo apt-get install telldus-core

§ sudo /etc/init.d/telldusd restart

sudo -u homeassistant bash
```

# Aliases

```
pi@pi2:~ $ cat .bash_aliases 
alias ha-logging='sudo journalctl --no-full -o cat -f -u home-assistant@pi'
alias ha-restart='sudo systemctl restart home-assistant@pi'
alias ha-update='sudo pip3 install --upgrade homeassistant'
alias ha-tellstick-restart='sudo /etc/init.d/telldusd restart'
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
