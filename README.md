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

## 33 Installing PHP

```bash
$ sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt
$ sudo nano /etc/apache2/mods-enabled/dir.conf
       <IfModule mod_dir.c>
             DirectoryIndex index.php index.html index.cgi ......
       </IfModule>  
$ sudo server apache2 restart
$ apt-cache search php5-
$ apt-cache show php5-json
$ sudo apt-get install php5-json
$ sudo nano /var/www/html/index.php
    <?php
    echo("Hey baby!");
    ?>
$ sudo nano /var/www/html/info.php
    <?php
    phpinfo();
    ?>

```

## 34 Installing PhpMyAdmin

```bash
$ sudo apt-get install phpmyadmin  # should config by step
$ sudo php5enmod mcrypt
$ sudo cp /etc/phpmyadmin/apache.conf /etc/apache2/conf-enabled/phpmyadmin.conf
$ sudo server apache2 restart
```

