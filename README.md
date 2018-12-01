# computer-networking
this is the basic knowledge of computer networking



## 31 Setting up a Firewall

```bash
$ sudo ufw allow 22/tcp  # 开放 ssh
$ sudo ufw allow 80/tcp  # 开放 http
$ sudo ufw allow 443/tcp # 开放 https
$ sudo ufw show added    # to check
$ sudo ufw enable        # to enable, maybe should choice timezone
```

## 32 Installing Apache and MySQL

```bash
$ sudo apt-get update
$ sudo apt-get apache2
$ sudo apt-get install mysql-server php5-mysql  # php5-mysql only for php
$ sudo mysql_secure_installation
```

