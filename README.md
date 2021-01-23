# Firejail Cheat Sheet
Firejail Cheat Sheet with the most needed stuff..

# Guides
- https://null-byte.wonderhowto.com/how-to/locking-down-linux-using-ubuntu-as-your-primary-os-part-3-application-hardening-sandboxing-0185710/
- https://www.youtube.com/watch?v=PQo9PEdVuIw

<br><br>

# Install
```bash
sudo apt-get install apparmor-profiles apparmor-utils
sudo aa-enforce /etc/apparmor.d/*
sudo apt install firejail
```
<br><br>

# paramater
- https://firejail.wordpress.com/features-3/man-firejail/


<br><br>

# start application in sandbox


<br><br>

## firefox
firejail --private-cache --nodbus --nogroups --caps.drop=all --noprofile --noroot --nou2f --notv --nodvd --noautopulse --no3d --disable-mnt --machine-id --seccomp --nonewprivs --apparmor --dns=103.86.96.100 --private-tmp firefox


<br><br>

## google-chrome (Chrome and Chromium got for default seccomp)
firejail --private-cache --nodbus --nogroups --caps.drop=all --noprofile --noroot --nou2f --notv --nodvd --noautopulse --no3d --disable-mnt --machine-id --nonewprivs --private-tmp --apparmor --dns=103.86.96.100 google-chrome


<br><br>

## use x11
--x11=xorg

<br><br>

## start application in sandbox and create a new /root and /home/user directories in temporary filesystems. All modifications are discarded when the sandbox is closed.
--private --private-dev --private-tmp --private-cache --private-bin=bash,sed,ls,cat --private-cwd --private-etc=group,hostname,localtime,nsswitch.conf,passwd,resolv.conf,default/motd-news


<br><br>

## disable internet access
--net=none --mac=69:69:69:69:69:69 --memory-deny-write-execute
