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

### Shells

- Interfaces to Linux systems
- Enviroments for running programs
- Switch between them
- Many options
  - bash
  - zsh, ksh, tcsh

```sh
# avaliable shells
cat /etc/shells
# current shell
echo $0
# change shell
chsh
```

### Navigating directories with _cd_

```sh
# print working dir
pwd
# cd /home
cd
cd ..
cd ../..
cd /
cd /home/mario
```

### Listing files with _ls_

- Lists files in current directory
- Options

```sh
ls /home/mario
# show hidden files
ls -a
# long format results
ls -l
# both options
ls -la
# sort by time and date
ls -t
# sort by extension
ls -X
# recursive tree list
ls -R
```

### Using _cat_ to read files

View files cointents

```sh
cat pets.txt
```

### Writing and combining files with _cat_

```sh
# write in file
cat >test3
hi
mario
ctrl+C
# view content
cat test3
# combining files
cat men-names women-names > all-names
cat all-names
```

### _man_

```sh
man cat
cat -n all-names
```

### Creating new directories with _mkdir_

```sh
mkdir mario
ls
cd mario
mkdir lazzari
mkdir {dir1,dir2,dir3,dir4}
mkdir -v test-dir
```

### How to copy files and directories with _cp_

```sh
cp file1 file2
cp -r dir1 dir2
cp --help | less
# backup destination file
cp -b file1 file2 # file2
```

### Deleting files with _rm_

```sh
# delete file
rm deleteme
# delete dir
rm deleteme
# delete dir and content
rm -r deleteme
# confirmation -i
rm -ri deleteme
# use wild cards
rm *.txt
```

### Moving files with _mv_

```sh
touch homewor
mv homewor homework
mv file dest_dir
cd dest_dir
ls
# confirmation
mv -i
```

### Sudo & root

#### Root account

- Superuser
- Kost privileged user
  - Software installation
  - Files ownerships
- Do use this accoutn for daily job
  - Security risks
  - Mistakes

#### _sudo_

- Allows you to run commands as another users
- Amministrations grants
- Root disabled by default on Ubuntu
- Add user to suduers
  - usermod -aG sudo mario
  - sudo command
  - sudo -u whoami username

### Finding files

find <start path> -name 'search'

```sh
find /home/mario -name 'homework'
# case insensitive
find /home/mario -iname 'homework'
find / -iname '*openssh*'
```

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

### _grep_

```sh
grep 'mario' admin-users
# case insensitive
grep -i 'Mario' admin-users
grep '192.168.1.1' *
# recursive
grep -r '192.168.1.1' *
# count rows
grep -c '192.168.1.1' *
grep -ci '192.168.1.1' *
echo $HOME
grep -r 'mario' $HOME
```

### Edit files with _nano_

```sh
nano
```

### Comparing two files with _diff_

```sh
diff file1 file2
diff -s file1 file2
# side by side
diff -y file1 file2
# directories
diff dir1 dir2
```

### Archiving files with _tar_

```sh
# c->create, v->verbose, f->file
tar -cvf backup.tarfile1 file2 file3
# archive dir
tac -cvf config.tar /home/mario/config
# untar: x->extract in current directory
tac -xvf config.tar
# -C-> destination
tac -xvf config.tar -C /home/mario/destination
```

### How to compress files

```sh
# Gzip
tac -cvzf config.tar.gz /home/mario/config
# bzip2
tac -cvjf config.tar.bzip2 /home/mario/config
```

### Changing user & root passwords

```sh
# change current user password
passwd
# change user passord
sudo passwd mario
sudo passwd root
```

### Switching users with _su_

```sh
su - mario
whoami
# root. - -> full login and change home
su -
```

### Changing your _hostname_

```sh
sudo cat /etc/hostname
hostname
sudo nano /etc/hostname
sudo nano /etc/hosts
sudo reboot
```

### Challenge #1

```sh
# task1
cat /etc/hostname
nano /etc/hostname
cat /etc/hostname
nano /etc/hosts
cat /etc/hosts
reboot
hostname

# task2
ls
mkdir backup
mkdir -p main/ oldfiles
cd main
ls
cd ..

# task3
touch /main/oldfiles/fileA
touch /main/oldfiles/fileB
touch /main/oldfiles/fileC

# task4
cd
nano /main/oldfile/fileA
diff -y oldcfg.txt newcfg.txt

# task5
echo $0
ps -p $$

# task6
passwd

# task7
cd /home
ls mario/main
rm -ri mario/main

# task8
find /home -iname '*.txt'

# task9
cd
find . -iname 'm.*' -type d
```

## Intermediate

### Installing software

```sh
sudo apt update
sudo apt install nmap
apt list --upgradeable
sudo apt upgrade
apt list --installed | less
```

### Removing / unistalling software

```sh
sudo apt remove apache2
# remove config files
sudo apt purge apache2
```

### Output redirection

| Overwrite | Stream | Append |
| --------- | ------ | ------ |
| >         | stdout | >>     |
| <         | stdin  | <<     |
| 2>        | stderr | 2>>    |

```sh
find / -name "*.sh" > log.txt
ls > files.txt
ls % 2> err.txt
```

### Output redirection lab

```sh

```
