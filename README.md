# computer-networking
this is the basic knowledge of computer networking

## 1 What is computer networking

**Computer networking** is an engineering discipline that aims to study and analyze the communication process among various computing devices or computer systems that are linked, or networked, together to exchange information and share resources.

Computer networking depends on the theoretical application and practical implementation of fields like computer engineering, computer sciences, information technology and telecommunication.

## 2,3,4 Types of Networks

Reach / Size

- LAN (Local Area Network) 局域网
- MAN (Metropolitan Area Network) 城域网
- WAN (Wide Area Network) 广域网 eg: "Internet"

## 5 Parts of a Network

- PC
- Server
- Printer
- routers（路由器）
- modem（调制解调器）
- ...

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

## 35 Securing PhpMyAdmin with htaccess

```bash
$ sudo nano /etc/apache2/conf-enabled/phpmyadmin.conf
   <Directory /usr/share/phpmyadmin>
        .....
        AllowOverride All
   <Directory>
$ sudo server apache2 restart
$ sudo nano /usr/share/phpmyadmin/.htaccess
	AuthTuype Basic
	AuthName "Restricted Files"
	AuthUserFile /etc/phpmyadmin/.htaccess
	Require valid-user
$ sudo apt-get install apache2-utils
$ sudo htpasswd -c /etc/phpmyadmin/.htpasswd shiinlee  # then to config password
```

## 36 Using SFTP or FTP

## 37 DHCP (Dynamic Host Configuration Protocol）

wikipedia: [DHCP](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol)

- ### discovery

- ### offer

- ### request

- ### acknowledgement

-  information
-  releasing

## 38 DNS

wikipedia: [DNS](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F)

## 39 Routing Tables Explained

```bash
$ route
$ 54.123.2.2
Destination   Gateway      Genmask        Flags  Mettric  Ref Use  Iface
default       192.168.0.1  0.0.0.0        UG     1024     0   0    eth0
192.168.0.0   *            255.255.255.0  U      0        0   0    wlan0
```

## 40 iptables Firewall Rules

```bash
$ iptables -L  # list iptables
Chain INPUT ......

Chain FORWARD .....

$ iptables -P FORWARD DROP  # this is to change `FORWARD` pocicy to DROP
$ iptables -L

$ iptables -A INPUT -s 192.168.0.23 -j DROP  # this is to block the 192.168.0.23, it can't connect my computer anymore

$ iptables -A INPUT -s 192.168.0.0/24 -p tcp --destination-port 25 -j DROP  # DROP the 192.168.0.0/24 tcp connection of smtp(mail) 

$ iptables -A INPUT -s 192.168.66 -j ACCEPT  # this like white list
$ iptables -D INPUT 3  # delete the third one
$ iptables -I INPUT -s 192.168.66 -j ACCEPT  # -I, add it to the top of the list

```

