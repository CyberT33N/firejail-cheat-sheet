# Firejail Cheat Sheet
Firejail Cheat Sheet with the most needed stuff..

# Good 2 know
- It does not work with apps that get installed through snap store as example:
```bash
sudo snap install spotify
```
  - because snap apps got their own sandbox












<br><br>
___________________________________________
___________________________________________
<br><br>

# Guides
- https://null-byte.wonderhowto.com/how-to/locking-down-linux-using-ubuntu-as-your-primary-os-part-3-application-hardening-sandboxing-0185710/
- https://www.youtube.com/watch?v=PQo9PEdVuIw



















<br><br>
___________________________________________
___________________________________________
<br><br>


# Install
```bash
sudo apt-get install apparmor-profiles apparmor-utils
sudo aa-enforce /etc/apparmor.d/*
sudo apt install firejail
```













<br><br>
___________________________________________
___________________________________________
<br><br>

# paramater

<br><br>

## CLI
- https://firejail.wordpress.com/features-3/man-firejail/

<br><br>

## .profile
- https://firejail.wordpress.com/features-3/man-firejail-profile/






















<br><br>
___________________________________________
___________________________________________
<br><br>

# start application in sandbox


<br><br>

## firefox
```bash
firejail --private-cache --nodbus --nogroups --caps.drop=all --noprofile --noroot --nou2f --notv --nodvd --noautopulse --no3d --disable-mnt --machine-id --seccomp --nonewprivs --apparmor --dns=103.86.96.100 --private-tmp firefox
```

<br><br>

## google-chrome (Chrome and Chromium got for default seccomp)
```bash
firejail --private-cache --nodbus --nogroups --caps.drop=all --noprofile --noroot --nou2f --notv --nodvd --noautopulse --no3d --disable-mnt --machine-id --nonewprivs --private-tmp --apparmor --dns=103.86.96.100 google-chrome
```


<br><br>

## spotify
```bash
firejail --private-cache --nodbus --nogroups --caps.drop=all --noprofile --noroot --nou2f --notv --nodvd --noautopulse --no3d --disable-mnt --machine-id --seccomp --nonewprivs --apparmor --dns=103.86.96.100 --private-tmp spotify --disable-gpu --disable-software-rasterizer --no-zygote
```


<br><br>

## use x11
```bash
--x11=xorg
```

<br><br>

## start application in sandbox and create a new /root and /home/user directories in temporary filesystems. All modifications are discarded when the sandbox is closed.
```bash
--private --private-dev --private-tmp --private-cache --private-bin=bash,sed,ls,cat --private-cwd --private-etc=group,hostname,localtime,nsswitch.conf,passwd,resolv.conf,default/motd-news
```

<br><br>

## disable internet access
```bash
--net=none --mac=69:69:69:69:69:69 --memory-deny-write-execute
```


































<br><br>
___________________________________________
___________________________________________
<br><br>

# Autostart 

a) Create a .profile file inside of /etc/firejail
- There are the default profiles stored.

b)
1. Create a file like **yourappname.profile** inside of **~/.config/firejail**
<br>2. Make sure that your .profile file has the exactly name like your app so as example firefox.profile
<br>3. Edit your File and edit Rights look below for examples
<br>4.
```bash
firejail yourapp
```
<br>5.
```bash
sudo firecfg
```
<br>6. At the next start the app will use your profile file.










<br><br>
<br><br>

## google-chrome.profile
```bash
# Firejail profile for default
# This file is overwritten after every install/update
# Persistent local customizations
include default.local
# Persistent global definitions
include globals.local

# generic gui profile
# depending on your usage, you can enable some of the commands below:

include disable-common.inc
include disable-devel.inc
include disable-exec.inc
include disable-interpreters.inc
# include disable-passwdmgr.inc
# include disable-programs.inc
include disable-xdg.inc




# apparmor
caps.drop all
# ipc-namespace
machine-id
# net none
# netfilter
no3d
nodbus
nodvd






nogroups
nonewprivs
noroot
noautopulse
# nosound
notv
nou2f
# novideo
protocol unix,inet,inet6
# shell none
# tracelog

# not working with chromium because its there for default
# seccomp

disable-mnt
# private
# private-bin program

private-cache
# private-dev
# private-etc alternatives
# private-lib
# private-tmp

# memory-deny-write-execute

dns 103.86.96.100
```




<br><br>
<br><br>


#### Recommended
- It is recommend to download srwiron .deb file and install it with sudo dpkg -i xxx.deb
  -  Then create **~/.config/firejail/chrome.profile** and use this Code here for creating shortcut on your desktop.
    ```
    touch ~/Desktop/iron.desktop
    
    sudo nano ~/Desktop/iron.desktop
    
    #!/usr/bin/env xdg-open
    [Desktop Entry]
    Name=Iron [Sandboxed]
    Exec=/bin/bash -c "firejail /usr/share/iron/chrome"
    Type=Application
    Terminal=true
    Icon=/home/t33n/Downloads/chromium-logo.png
    ```
    - If chrome is not starting the you must disable sandbox with --no-sandbox















<br><br>
<br><br>
<br><br>
<br><br>




## spotify.profile
```bash
# Firejail profile for default
# This file is overwritten after every install/update
# Persistent local customizations
include default.local
# Persistent global definitions
include globals.local

# generic gui profile
# depending on your usage, you can enable some of the commands below:

include disable-common.inc
include disable-devel.inc
include disable-exec.inc
include disable-interpreters.inc
# include disable-passwdmgr.inc
# include disable-programs.inc
include disable-xdg.inc




# apparmor
caps.drop all
# ipc-namespace
machine-id
# net none
# netfilter
no3d
nodbus
nodvd






nogroups
nonewprivs
noroot
noautopulse
# nosound
notv
nou2f
# novideo
protocol unix,inet,inet6
# shell none
# tracelog

# not working with chromium because its there for default
# seccomp

disable-mnt
# private
# private-bin program

private-cache
# private-dev
# private-etc alternatives
# private-lib
# private-tmp

# memory-deny-write-execute

dns 103.86.96.100
```

















<br><br>

## firefox.profile
```bash
# Firejail profile for default
# This file is overwritten after every install/update
# Persistent local customizations
include default.local
# Persistent global definitions
include globals.local

# generic gui profile
# depending on your usage, you can enable some of the commands below:

include disable-common.inc
include disable-devel.inc
include disable-exec.inc
include disable-interpreters.inc
# include disable-passwdmgr.inc
# include disable-programs.inc
include disable-xdg.inc




# apparmor
caps.drop all
# ipc-namespace
machine-id
# net none
# netfilter
no3d
nodbus
nodvd

nogroups
nonewprivs
noroot
noautopulse
# nosound
notv
nou2f
# novideo
protocol unix,inet,inet6
# shell none
# tracelog
seccomp
disable-mnt
# private
# private-bin program

private-cache
# private-dev
# private-etc alternatives
# private-lib
# private-tmp

# memory-deny-write-execute

dns 103.86.96.100
```




<br><br>

## discord.profile
```bash
# Firejail profile for default
# This file is overwritten after every install/update
# Persistent local customizations
include default.local
# Persistent global definitions
include globals.local

# generic gui profile
# depending on your usage, you can enable some of the commands below:

include disable-common.inc
include disable-devel.inc
# include disable-exec.inc
include disable-interpreters.inc
# include disable-passwdmgr.inc
# include disable-programs.inc
include disable-xdg.inc




# apparmor
caps.drop all
# ipc-namespace
machine-id
# net none
# netfilter
no3d
nodbus
nodvd






nogroups
nonewprivs
noroot
noautopulse
# nosound
notv
nou2f
# novideo
protocol unix,inet,inet6
# shell none
# tracelog

# not working with chromium because its there for default
# seccomp

disable-mnt
# private
# private-bin program

private-cache
# private-dev
# private-etc alternatives
# private-lib
# private-tmp

# memory-deny-write-execute

dns 103.86.96.100
```
