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

## 6 How the Internet Works

PC --- Server --- Laptop

## 7 Server

## 8 Clients and Hosts

“client”                                     "Host"

  P.C.   —————————  Web Server

## 9 Network Interface Card (NIC)

```
A Network Interface Card (NIC) is a computer hardware component that allows a computer to connect to a network. NICs may be used for both wired and wireless connections.

A NIC is also known as a network interface controller (NIC), network interface controller card, expansion card, computer circuit board, network card, LAN card, network adapter or network adapter card (NAC).
```

[**NIC**](https://en.wikipedia.org/wiki/Network_interface_controller)

## 10 What is Protocol?  什么是协议？

```
A protocol is a set of rules and guidelines for communicating data. Rules are defined for each step and process during communication between two or more computers. Networks have to follow these rules to successfully transmit data.
```

## 11 Protocols

```
http://www.google.com/index.html

http: protocol
www.google.com: server name
index.html: file
```

## 12 Bus Topology

```
Bus topology is a specific kind of network topology in which all of the various devices in the network are connected to a single cable or line. In general, the term refers to how various devices are set up in a network.
```

```
"BUS":

        "PC"              "MAC"
"T"  ------------------------------ "Terminal"
               "Laptop"
```

## 13 Ring Topology

```
A ring topology is a network configuration in which device connections create a circular data path. Each networked device is connected to two others, like points on a circle. Together, devices in a ring topology are referred to as a ring network.
```

## 14 Star Topology

```
Alternatively referred to as a star network, star topology is one of the most common network setups. In this configuration, every node connects to a central network device, like a hub, switch, or computer. The central network device acts as a server and the peripheral devices act as clients. Depending on the type of network card used in each computer of the star topology, a coaxial cable or an RJ-45 network cable is used to connect computers together.
```

## 15 Mesh Topology

```
A network setup where each computer and network device is interconnected with one another, allowing for most transmissions to be distributed even if one of the connections go down. It is a topology commonly used for wireless networks. Below is a visual example of a simple computer setup on a network using a mesh topology.
```

## 16,17 OSI Model

- Applications   (firefox / chrome / email)
- Presentation  (O.S. / letters # numberts  --> ASCII)
- Session  (Conversion between 2 computers)
- Transport  (packages/datas are dilivered reliably)
- Network  (Determine best roure for data)
- Data Link  (NIC's / checking for error)
- Physical  (Cable / fiber-optics / Electric Signals)

## 18 Modem (调制解调器）

[Modem](https://techterms.com/definition/modem)

## 19 Router

## 20 Switch

It gives us more ports.

[Switch](https://en.wikipedia.org/wiki/Network_switch)

## 21 Repeater

```
A repeater is a network device that retransmits a received signal with more power and to an extended geographical or topological network boundary than what would be capable with the original signal.
```

## 22 How Binary Code works

0 ~ 255

128 64 32 16 8 4 2 1 0

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

