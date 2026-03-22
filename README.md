# Learn Ubuntu

## Networking

### Viewing IP

Note: ifconfig / ipconfig deprecated: available in net-tools package

```sh
ip a
ls /etc/netplan/ # netplan configuration
cat /etc/netplan/*
ip route # default routes

```

### Enabling SSH

```sh
sudo apt update
sudo apt install openssh-server
sudo systemctl status ssh
sudo systemctl start ssh
ip a
sudo nano /etc/ssh/sshd_config
sudo systemctl restart ssh
```

### Static IP

```sh
netplan
cd /etc/netplan
ls
nano 01-network-manager-all.yaml
sudo netplan apply
ip a
```

```yaml
# /etc/netplan/01-static.yaml
network:
  version: 2
  renderer: networkd

  ethernets:
    eth0:
      dhcp4: false
      addresses:
        - 192.168.1.100/24
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
          - 1.1.1.1
```

### ipconfig vs ip addr

#### ifconfig vs ip addr

If you've dabbled in Linux before, you might be familiar with the "ifconfig" command. This is somewhat equivalent to the "ipconfig" command in Windows, and lets you view IP configuration in Linux, and also assign static IP addresses. That said, the ifconfig command is being deprecated in linux, in favor of the ip addr command (or "ip a" as I prefer to type!)

#### /etc/network/interfaces

In the previous versions of Ubuntu, you managed your network interfaces with a file called "interfaces" located at /etc/network. In 20.04 and moving forward, the preferred method is to leverage netplan (as I demonstrate on the 'Setting a static IP' lesson). If you'd like to revert back to the old way of managing your networking (and not use netplan), you can follow the instructions at the blog in the resources section of this article.
