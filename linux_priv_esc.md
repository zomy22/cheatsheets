### Linux Privilege Escalation CheatSheet

Shell upgrade

```
python -c 'import pty; pty.spawn("/bin/bash")'
python3 -c 'import pty; pty.spawn("/bin/bash")'
(Ctrl+Z)
stty raw -echo
fg
<Enter>
<Enter>
export TERM=xterm
```


OS, Kernel & Hostname:

```
cat /etc/issue
cat /proc/version
hostname
uname -a
cat /etc/redhat-release
```

Users:

```
cat /etc/passwd
REUSE PASSWORDS THAT YOU ALREADY HAVE !

id
who
w
Sudo
sudo -l
```

Networking information:

```
ifconfig -a

route

netstat -antup

arp -e

Applications and services

ps aux

ps aux | grep root

```

Installed Applications:

```
dpkg -l # Debian derivatives

rpm -qa # Fedora based distros use

ls -ls /etc/ | grep .conf

ls -ls /var/www/html/
```

SUID programs on a given system:

```
find /* -user root -perm -4000 -print 2>/dev/null
```
Files and file system permissions:

```
# Check for unmounted file system
cat /etc/fstab

# World writable directories:
find / \( -wholename '/home/homedir*' -prune \) -o \( -type d -perm -0002 \) -exec ls -ld '{}' ';' 2>/dev/null | grep -v root

# World writable directories for root:
find / \( -wholename '/home/homedir*' -prune \) -o \( -type d -perm -0002 \) -exec ls -ld '{}' ';' 2>/dev/null | grep root

# World writable files:
find / \( -wholename '/home/homedir/*' -prune -o -wholename '/proc/*' -prune \) -o \( -type f -perm -0002 \) -exec ls -l '{}' ';' 2>/dev/null

# These next commands print the search results to the terminal without any additional information.
# Find world writable files in /etc:

find /etc -perm -2 -type f 2>/dev/null

# And the following command searches for world writable directories:

find / -writable -type d 2>/dev/null
```

Kernel exploits conditions: 

1. A vulnerable kernel
2. A working exploit  ( working also for your Operating system eg "searchsploit linux kernel 3. --exclude="/dos/" centos" ) 
3. A way to transfer the exploit to the target;
4. A way to compile the exploit;
5. A way to execute the exploit.

In general, with the exception of point 4 these requirements apply to most kernel attacks.


### References and extra resources

https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/

LinPEAS:
https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS

Linux privilege escalation checker: 
```
wget http://www.securitysift.com/download/linuxprivchecker.py
```
unix-privesc-check: 
https://github.com/pentestmonkey/unix-privesc-check


