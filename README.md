# Learn Ubuntu

- 1. [Introduction](#Introduction)
  - 1.1. [File system](#Filesystem)
  - 1.2. [Linux Directory Reference](#LinuxDirectoryReference)
    - 1.2.1. [/bin](#bin)
    - 1.2.2. [/sbin](#sbin)
    - 1.2.3. [/boot](#boot)
    - 1.2.4. [/dev](#dev)
    - 1.2.5. [/etc](#etc)
    - 1.2.6. [/home](#home)
    - 1.2.7. [/lib & /lib64](#liblib64)
    - 1.2.8. [/media](#media)
    - 1.2.9. [/mnt](#mnt)
    - 1.2.10. [/opt](#opt)
    - 1.2.11. [/proc](#proc)
    - 1.2.12. [/root](#root)
    - 1.2.13. [/sys](#sys)
    - 1.2.14. [/tmp](#tmp)
    - 1.2.15. [/usr](#usr)
    - 1.2.16. [/var](#var)
  - 1.3. [Shells](#Shells)
  - 1.4. [Navigating directories with _cd_](#Navigatingdirectorieswith_cd_)
  - 1.5. [Listing files with _ls_](#Listingfileswith_ls_)
  - 1.6. [Using _cat_ to read files](#Using_cat_toreadfiles)
  - 1.7. [Writing and combining files with _cat_](#Writingandcombiningfileswith_cat_)
  - 1.8. [_man_](#man_)
  - 1.9. [Creating new directories with _mkdir_](#Creatingnewdirectorieswith_mkdir_)
  - 1.10. [How to copy files and directories with _cp_](#Howtocopyfilesanddirectorieswith_cp_)
  - 1.11. [Deleting files with _rm_](#Deletingfileswith_rm_)
  - 1.12. [Moving files with _mv_](#Movingfileswith_mv_)
  - 1.13. [Sudo & root](#Sudoroot)
    - 1.13.1. [Root account](#Rootaccount)
    - 1.13.2. [_sudo_](#sudo_)
  - 1.14. [Finding files](#Findingfiles)
  - 1.15. [_grep_](#grep_)
  - 1.16. [Edit files with _nano_](#Editfileswith_nano_)
  - 1.17. [Comparing two files with _diff_](#Comparingtwofileswith_diff_)
  - 1.18. [Archiving files with _tar_](#Archivingfileswith_tar_)
  - 1.19. [How to compress files](#Howtocompressfiles)
  - 1.20. [Changing user & root passwords](#Changinguserrootpasswords)
  - 1.21. [Switching users with _su_](#Switchinguserswith_su_)
  - 1.22. [Changing your _hostname_](#Changingyour_hostname_)
  - 1.23. [Challenge #1](#Challenge1)
- 2. [Intermediate](#Intermediate)
  - 2.1. [Installing software](#Installingsoftware)
  - 2.2. [Removing / unistalling software](#Removingunistallingsoftware)
  - 2.3. [Output redirection](#Outputredirection)
  - 2.4. [Output redirection lab](#Outputredirectionlab)
  - 2.5. [Output redirection with _pipes_](#Outputredirectionwith_pipes_)
    - 2.5.1. [What is pipe?](#Whatispipe)
  - 2.6. [How to _sort_](#Howto_sort_)
  - 2.7. [Editing with _sed_](#Editingwith_sed_)
  - 2.8. [Links](#Links)
  - 2.9. [Create new user](#Createnewuser)
  - 2.10. [User groups](#Usergroups)
  - 2.11. [Permissions with _chmod_](#Permissionswith_chmod_)
  - 2.12. [Ownerships with _chown_](#Ownershipswith_chown_)
  - 2.13. [Shutdown and reboot](#Shutdownandreboot)
  - 2.14. [Aliases](#Aliases)
  - 2.15. [Challenge lab 2](#Challengelab2)
- 3. [Networking](#Networking)
  - 3.1. [ipconfig vs ip addr](#ipconfigvsipaddr)
    - 3.1.1. [ifconfig vs ip addr](#ifconfigvsipaddr)
    - 3.1.2. [/etc/network/interfaces](#etcnetworkinterfaces)
  - 3.2. [IP informations](#IPinformations)
  - 3.3. [SSH](#SSH)
  - 3.4. [Static IP](#StaticIP)
  - 3.5. [ipconfic vs ip](#ipconficvsip)
    - 3.5.1. [ifconfig vs ip addr](#ifconfigvsipaddr-1)
    - 3.5.2. [/etc/network/interfaces](#etcnetworkinterfaces-1)
  - 3.6. [Enable interface](#Enableinterface)
  - 3.7. [Public key authentication](#Publickeyauthentication)
  - 3.8. [DNS](#DNS)
  - 3.9. [Downloading files with _curl_ and _wget_](#Downloadingfileswith_curl_and_wget_)
  - 3.10. [FTP](#FTP)
  - 3.11. [SCP](#SCP)
- 4. [Shell scripting](#Shellscripting)
  - 4.1. [First script](#Firstscript)
  - 4.2. [PATH](#PATH)
  - 4.3. [Cron jobs](#Cronjobs)
- 5. [Troubleshoting](#Troubleshoting)
  - 5.1. [Monitoring logs with _tail_](#Monitoringlogswith_tail_)
  - 5.2. [Checking disk space with _df_](#Checkingdiskspacewith_df_)
  - 5.3. [Monitoring with _watch_](#Monitoringwith_watch_)
  - 5.4. [Active network connections with _ss_](#Activenetworkconnectionswith_ss_)
  - 5.5. [Network trubleshooting with _tcpdumping_](#Networktrubleshootingwith_tcpdumping_)

## 1. <a name='Introduction'></a>Introduction

### 1.1. <a name='Filesystem'></a>File system

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

### 1.2. <a name='LinuxDirectoryReference'></a>Linux Directory Reference

In the last lesson, we discussed some of the common directories you'll see inside of Ubuntu throughout this course. These directories are found in most Linux distributions, so it's important to at least have a very high level understanding of what they're used for! Let's look at some of the common ones:

#### 1.2.1. <a name='bin'></a>/bin

Used to store critical binaries used within the Linux kernel. When you type a command in the terminal, this is the directory which is searched through. For example, if you type "ls" - there is actually an "ls" binary inside of /bin that is executed when you enter that command.

#### 1.2.2. <a name='sbin'></a>/sbin

Very similar to /bin, /sbin is used primarily for system binaries (sbin), which are utilities and binaries that are typically used by root/privileged users and not normal users. These are things like route, ifconfig, and fdisk. which are all used to manage networking, disk formatting, and a lot more.

#### 1.2.3. <a name='boot'></a>/boot

Files in this directory are needed for the system to boot. This directory should rarely, if ever be touched, or else you risk your system having issues starting up!

#### 1.2.4. <a name='dev'></a>/dev

Stands for "device," and not developer! This is where hardware devices are represented in the system, such as CPU, serial lines, hard drives, cdrom, and more.

#### 1.2.5. <a name='etc'></a>/etc

System settings and configuration. If you want to change things like hostname, DNS/nameserver settings, or IP address configuration, those will all be found inside of /etc.

#### 1.2.6. <a name='home'></a>/home

User files will be found inside of /home. These would be things such as documents, photos, text files, etc - and each user will automatically get their own home directory when the user is created. For example, user "mike" would be located at /home/mike.

#### 1.2.7. <a name='liblib64'></a>/lib & /lib64

Critical system files, such as library images that are used to aid in system boot.

#### 1.2.8. <a name='media'></a>/media

Everything inside of linux is treated as a file, including external media - such as thumb drives and CD ROM disks! If you were to plug a usb thumb drive into your linux system, in most cases, you would then see an entry in /media appear.

#### 1.2.9. <a name='mnt'></a>/mnt

Used to temporarily mount USB drives, or ISO images. Mounting essentially makes external files accessible on the system by giving them a directory that they can be accessed at.

#### 1.2.10. <a name='opt'></a>/opt

Used by third party software, for plugins and such - stands for "Optional"

#### 1.2.11. <a name='proc'></a>/proc

Information about running processes. The entries here are not necessarily files, they are essentially placeholders to access system information, such as CPU info (found at /proc/cpuinfo).

#### 1.2.12. <a name='root'></a>/root

Used as the root users home directory. Meant to remain separate from user home directories for security purposes.

#### 1.2.13. <a name='sys'></a>/sys

Used as a virtual filesystem, this directory shows information related to kernel subsystems, hardware devices, and device drivers.

#### 1.2.14. <a name='tmp'></a>/tmp

Used for temporary files, such as crash logs, install logs, etc.

#### 1.2.15. <a name='usr'></a>/usr

Contains subdirectories with commands that are considered nonessential to the linux operating system, as well as header files which are used to compile C programs.

#### 1.2.16. <a name='var'></a>/var

Used for variable data, such as logs, databases, and temporary spool (email, printing). This is an important directory because it contains /var/log which is where most logs are stored.

### 1.3. <a name='Shells'></a>Shells

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

### 1.4. <a name='Navigatingdirectorieswith_cd_'></a>Navigating directories with _cd_

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

### 1.5. <a name='Listingfileswith_ls_'></a>Listing files with _ls_

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

### 1.6. <a name='Using_cat_toreadfiles'></a>Using _cat_ to read files

View files cointents

```sh
cat pets.txt
```

### 1.7. <a name='Writingandcombiningfileswith_cat_'></a>Writing and combining files with _cat_

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

### 1.8. <a name='man_'></a>_man_

```sh
man cat
cat -n all-names
```

### 1.9. <a name='Creatingnewdirectorieswith_mkdir_'></a>Creating new directories with _mkdir_

```sh
mkdir mario
ls
cd mario
mkdir lazzari
mkdir {dir1,dir2,dir3,dir4}
mkdir -v test-dir
```

### 1.10. <a name='Howtocopyfilesanddirectorieswith_cp_'></a>How to copy files and directories with _cp_

```sh
cp file1 file2
cp -r dir1 dir2
cp --help | less
# backup destination file
cp -b file1 file2 # file2
```

### 1.11. <a name='Deletingfileswith_rm_'></a>Deleting files with _rm_

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

### 1.12. <a name='Movingfileswith_mv_'></a>Moving files with _mv_

```sh
touch homewor
mv homewor homework
mv file dest_dir
cd dest_dir
ls
# confirmation
mv -i
```

### 1.13. <a name='Sudoroot'></a>Sudo & root

#### 1.13.1. <a name='Rootaccount'></a>Root account

- Superuser
- Kost privileged user
  - Software installation
  - Files ownerships
- Do use this accoutn for daily job
  - Security risks
  - Mistakes

#### 1.13.2. <a name='sudo_'></a>_sudo_

- Allows you to run commands as another users
- Amministrations grants
- Root disabled by default on Ubuntu
- Add user to suduers
  - usermod -aG sudo mario
  - sudo command
  - sudo -u whoami username

### 1.14. <a name='Findingfiles'></a>Finding files

find <start path> -name 'search'

```sh
find /home/mario -name 'homework'
# case insensitive
find /home/mario -iname 'homework'
find / -iname '*openssh*'
```

### 1.15. <a name='grep_'></a>_grep_

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

### 1.16. <a name='Editfileswith_nano_'></a>Edit files with _nano_

```sh
nano
```

### 1.17. <a name='Comparingtwofileswith_diff_'></a>Comparing two files with _diff_

```sh
diff file1 file2
diff -s file1 file2
# side by side
diff -y file1 file2
# directories
diff dir1 dir2
```

### 1.18. <a name='Archivingfileswith_tar_'></a>Archiving files with _tar_

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

### 1.19. <a name='Howtocompressfiles'></a>How to compress files

```sh
# Gzip
tac -cvzf config.tar.gz /home/mario/config
# bzip2
tac -cvjf config.tar.bzip2 /home/mario/config
```

### 1.20. <a name='Changinguserrootpasswords'></a>Changing user & root passwords

```sh
# change current user password
passwd
# change user passord
sudo passwd mario
sudo passwd root
```

### 1.21. <a name='Switchinguserswith_su_'></a>Switching users with _su_

```sh
su - mario
whoami
# root. - -> full login and change home
su -
```

### 1.22. <a name='Changingyour_hostname_'></a>Changing your _hostname_

```sh
sudo cat /etc/hostname
hostname
sudo nano /etc/hostname
sudo nano /etc/hosts
sudo reboot
```

### 1.23. <a name='Challenge1'></a>Challenge #1

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

## 2. <a name='Intermediate'></a>Intermediate

### 2.1. <a name='Installingsoftware'></a>Installing software

```sh
sudo apt update
sudo apt install nmap
apt list --upgradeable
sudo apt upgrade
apt list --installed | less
```

### 2.2. <a name='Removingunistallingsoftware'></a>Removing / unistalling software

```sh
sudo apt remove apache2
# remove config files
sudo apt purge apache2
```

### 2.3. <a name='Outputredirection'></a>Output redirection

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

### 2.4. <a name='Outputredirectionlab'></a>Output redirection lab

```sh
ls % 2> error.txt
cat error.txt
find / -name "*.sh" 2> log.txt
# avoid new file creation
find / -name "*.sh" 2> /dev/null
cat /dev/null
hostnamectl > host_details.txt
cat host_details.txt
# append
ls / >>files.txt
```

### 2.5. <a name='Outputredirectionwith_pipes_'></a>Output redirection with _pipes_

#### 2.5.1. <a name='Whatispipe'></a>What is pipe?

- Another form of redirection
- Redirect standard output to another command

```sh
la | grep 'mario'
# tee reads from stdin and writes on multiple stdout
echo "hello" | tee output.txt
```

### 2.6. <a name='Howto_sort_'></a>How to _sort_

```sh
sort countries
# save sorting
sort -o countries countries
# reverse sorting
sort -r countries
# remove duplicates
sort -u countries
man sort
# sort ls by 5th column
ls -l | sort -nk5
```

### 2.7. <a name='Editingwith_sed_'></a>Editing with _sed_

- Mutil tools
  - find & replace
  - insert
  - delete
- Edit file without open
- By default does not change file

```sh
# replace 1st
sed 's/foo/bar/' file.txt
# replace all
sed 's/foo/bar/g' file.txt
# update in place
sed -i 's/foo/bar/g' file.txt
# delete line number
sed -i '3d' file.txt
# replace 1st
sed '1 s/foo/bar/' file.txt
```

### 2.8. <a name='Links'></a>Links

- Shortcut to another file or directory
- Hard: file only
- Soft: file and directory

```sh
ln scripts/hello.sh hadr-hello.sh
ls -ila # i -> inode
ln scripts/hello.sh hard-hello.sh
ln -s scripts/hello.sh soft-hello.sh
ls -ila
```

### 2.9. <a name='Createnewuser'></a>Create new user

```sh
sudo adduser maria
```

### 2.10. <a name='Usergroups'></a>User groups

```sh
groups
groups mario
sudo adduser mario sudo
```

### 2.11. <a name='Permissionswith_chmod_'></a>Permissions with _chmod_

```sh
chmod 700 myfile.txt
chmod 666 file.txt
chmod 777 all.txt
```

### 2.12. <a name='Ownershipswith_chown_'></a>Ownerships with _chown_

```sh
sudo chown mario file.txt
sudo chgrp riit file.txt
```

### 2.13. <a name='Shutdownandreboot'></a>Shutdown and reboot

```sh
# shutdown in minutes
shutdown -h 5
# reboot
shutdown -r
# shutdown in minutes
shutdown +30
# cancel pending shutdown
shutdown -c
```

### 2.14. <a name='Aliases'></a>Aliases

Add aliases in _.bashrc_

```sh
alias reach='ping -c 4 1.1.1.1'
alias c='clear'
```

### 2.15. <a name='Challengelab2'></a>Challenge lab 2

```sh
apt install apache2
ls /var/www/html/index.html
sudo mv /var/www/html/index.html /var/www/html/index.html.old
grep -in 'remotedb' /etc/debconf.conf
sudo adduser dinesh
```

## 3. <a name='Networking'></a>Networking

### 3.1. <a name='ipconfigvsipaddr'></a>ipconfig vs ip addr

#### 3.1.1. <a name='ifconfigvsipaddr'></a>ifconfig vs ip addr

If you've dabbled in Linux before, you might be familiar with the "ifconfig" command. This is somewhat equivalent to the "ipconfig" command in Windows, and lets you view IP configuration in Linux, and also assign static IP addresses. That said, the ifconfig command is being deprecated in linux, in favor of the ip addr command (or "ip a" as I prefer to type!)

#### 3.1.2. <a name='etcnetworkinterfaces'></a>/etc/network/interfaces

In the previous versions of Ubuntu, you managed your network interfaces with a file called "interfaces" located at /etc/network. In 20.04 and moving forward, the preferred method is to leverage netplan (as I demonstrate on the 'Setting a static IP' lesson). If you'd like to revert back to the old way of managing your networking (and not use netplan), you can follow the instructions at the blog in the resources section of this article.

### 3.2. <a name='IPinformations'></a>IP informations

```sh
# deprecated
ifconfig
# new
ip a
ls /etc/netplan
cat /etc/netplan
ip route
```

### 3.3. <a name='SSH'></a>SSH

```sh
sudo apt install openssh-server
sudo systemctl status ssh
ssh mario@myserver
```

### 3.4. <a name='StaticIP'></a>Static IP

```sh
cd /etc/netplan
cat
```

```yaml
network:
  version: 2
  renderer: networkd

  ethernets:
    eth0:
      dhcp4: no
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

Older versions

```yaml
network:
  version: 2
  renderer: networkd

  ethernets:
    eth0:
      dhcp4: no
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
```

```sh
sudo netplan try
sudo netplan apply
```

### 3.5. <a name='ipconficvsip'></a>ipconfic vs ip

[doc](https://linuxconfig.org/how-to-switch-back-networking-to-etc-network-interfaces-on-ubuntu-20-04-focal-fossa-linux)

#### 3.5.1. <a name='ifconfigvsipaddr-1'></a>ifconfig vs ip addr

If you've dabbled in Linux before, you might be familiar with the "ifconfig" command. This is somewhat equivalent to the "ipconfig" command in Windows, and lets you view IP configuration in Linux, and also assign static IP addresses. That said, the ifconfig command is being deprecated in linux, in favor of the ip addr command (or "ip a" as I prefer to type!)

#### 3.5.2. <a name='etcnetworkinterfaces-1'></a>/etc/network/interfaces

In the previous versions of Ubuntu, you managed your network interfaces with a file called "interfaces" located at /etc/network. In 20.04 and moving forward, the preferred method is to leverage netplan (as I demonstrate on the 'Setting a static IP' lesson). If you'd like to revert back to the old way of managing your networking (and not use netplan), you can follow the instructions at the blog in the resources section of this article.

### 3.6. <a name='Enableinterface'></a>Enable interface

```sh
ip a | grep 'status'
sudo ip link set eth0 down
sudo ip link set eth0 up
```

### 3.7. <a name='Publickeyauthentication'></a>Public key authentication

```sh
cd
cd .ssh
ssh-keygen -t rsa
ssh-copy-id mario@mariolazzari.it
```

### 3.8. <a name='DNS'></a>DNS

```sh
cat /etc/hosts
systemd-resolve --status | grep Current
ping google.com
nslookup google.com
```

### 3.9. <a name='Downloadingfileswith_curl_and_wget_'></a>Downloading files with _curl_ and _wget_

- Multiple protocols
- No user interactions
- wget simpler
- curl more flexible

```sh
curl -I mariolazzari.it
curl -L mariolazzari.it
wget -P mario mariolazzari.it
```

### 3.10. <a name='FTP'></a>FTP

```sh
ftp
?
open speedtest.tele2.net
ls
get 2MB.zip
put 2MB.zip
exit
```

### 3.11. <a name='SCP'></a>SCP

```sh
# copy from remote server
scp mario@mariolazzari.it:file.txt .
# copy to remote server
scp filex.txt mario@mariolazzari.it:/home/mario
# copy entire dir
scp ./docs mario@mariolazzari.it:/home/mario/docs
```

## 4. <a name='Shellscripting'></a>Shell scripting

### 4.1. <a name='Firstscript'></a>First script

```sh
#!/bin/sh

# comment
echo "my first script"
```

```sh
chmod 755 first.sh
./first.sh
```

```sh
#!/bin/sh

echo "Enter new dir name"

read newdir

echo "New dir name: $newdir"

FULLPATH=$HOME/$newdir

mkdir $FULLPATH

echo "New dir created at: $FULLPATH"
```

### 4.2. <a name='PATH'></a>PATH

```sh
.bashrc
echo $PATH
```

### 4.3. <a name='Cronjobs'></a>Cron jobs

_cron_ runs a command at spicified time or interval
[Editor](https://crontab.guru/)

```
* * * * * command
│ │ │ │ │
│ │ │ │ └── week day (0-7, sunday = 0 o 7)
│ │ │ └──── month (1-12)
│ │ └────── day of month (1-31)
│ └──────── time (0-23)
└────────── minute (0-59)
```

```sh
# edit config
sudo crontab -e
# show config
crontab -l
# every day at 2:30
30 2 * * * /usr/local/bin/backup.sh
# every 5 minutes
*/5 * * * * /usr/bin/php /var/www/app/script.php
# Backup DB every night (with logging)
0 2 * * * /usr/local/bin/pg_backup.sh >> /var/log/pg_backup.log 2>&1
# cache cleaning every hour
0 * * * * /usr/local/bin/cache_cleanup.sh
```

## 5. <a name='Troubleshoting'></a>Troubleshoting

### 5.1. <a name='Monitoringlogswith_tail_'></a>Monitoring logs with _tail_

```sh
# show last 10 rows
tail logs.txt
# realtime
tail -f logs.txt
# last 50 rows
tail -n 50
# multiple files
tail file1 file2
```

### 5.2. <a name='Checkingdiskspacewith_df_'></a>Checking disk space with _df_

```sh
df
# human readable
df -h
```

### 5.3. <a name='Monitoringwith_watch_'></a>Monitoring with _watch_

Runs commands at regular time and displays outputs.

```sh
# watch date every 2 seconds
watch date
# since last update
watch -d date
# every 10 seconds
watch -n 10 date
```

### 5.4. <a name='Activenetworkconnectionswith_ss_'></a>Active network connections with _ss_

```sh
ss -ltpn

```

### 5.5. <a name='Networktrubleshootingwith_tcpdumping_'></a>Network trubleshooting with _tcpdumping_

```sh
# show available interfaces
sudo tcpdump -D
# specific interface
sudo tcpdump -i <interface>
# capture 5 packages
sudo tcpdump -c 5
# save to file
sudo tcpdump -w file.pcap
# ex
sudo tcpdump -i eth0 port:80
# capture all traffic from & to
sudo tcpdump host 192.168.1.1

```
