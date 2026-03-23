# Learn Ubuntu

## Hatchling

### File system

- / (root)
- /bin (binaries)
- /sbin (system binaries)
- /boot (kernel and bootloader)
- /dev (device files)

```sh
cd /
ls
ls bin
whoami
ls boot
ls etc
cat hostname
ls home
```

### Linux Directory Reference

In the last lesson, we discussed some of the common directories you'll see inside of Ubuntu throughout this course. These directories are found in most Linux distributions, so it's important to at least have a very high level understanding of what they're used for! Let's look at some of the common ones:

#### /bin

Used to store critical binaries used within the Linux kernel. When you type a command in the terminal, this is the directory which is searched through. For example, if you type "ls" - there is actually an "ls" binary inside of /bin that is executed when you enter that command.

#### /sbin

Very similar to /bin, /sbin is used primarily for system binaries (sbin), which are utilities and binaries that are typically used by root/privileged users and not normal users. These are things like route, ifconfig, and fdisk. which are all used to manage networking, disk formatting, and a lot more.

#### /boot

Files in this directory are needed for the system to boot. This directory should rarely, if ever be touched, or else you risk your system having issues starting up!

#### /dev

Stands for "device," and not developer! This is where hardware devices are represented in the system, such as CPU, serial lines, hard drives, cdrom, and more.

#### /etc

System settings and configuration. If you want to change things like hostname, DNS/nameserver settings, or IP address configuration, those will all be found inside of /etc.

#### /home

User files will be found inside of /home. These would be things such as documents, photos, text files, etc - and each user will automatically get their own home directory when the user is created. For example, user "mike" would be located at /home/mike.

#### /lib & /lib64

Critical system files, such as library images that are used to aid in system boot.

#### /media

Everything inside of linux is treated as a file, including external media - such as thumb drives and CD ROM disks! If you were to plug a usb thumb drive into your linux system, in most cases, you would then see an entry in /media appear.

#### /mnt

Used to temporarily mount USB drives, or ISO images. Mounting essentially makes external files accessible on the system by giving them a directory that they can be accessed at.

#### /opt

Used by third party software, for plugins and such - stands for "Optional"

#### /proc

Information about running processes. The entries here are not necessarily files, they are essentially placeholders to access system information, such as CPU info (found at /proc/cpuinfo).

#### /root

Used as the root users home directory. Meant to remain separate from user home directories for security purposes.

#### /sys

Used as a virtual filesystem, this directory shows information related to kernel subsystems, hardware devices, and device drivers.

#### /tmp

Used for temporary files, such as crash logs, install logs, etc.

#### /usr

Contains subdirectories with commands that are considered nonessential to the linux operating system, as well as header files which are used to compile C programs.

#### /var

Used for variable data, such as logs, databases, and temporary spool (email, printing). This is an important directory because it contains /var/log which is where most logs are stored.

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
