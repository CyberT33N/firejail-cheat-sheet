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

# CLI

- https://firejail.wordpress.com/features-3/man-firejail/
```
ptions:
    -- - signal the end of options and disables further option processing.
    --allow-debuggers - allow tools such as strace and gdb inside the sandbox.
    --allusers - all user home directories are visible inside the sandbox.
    --apparmor - enable AppArmor confinement with the default profile.
    --apparmor=profile_name - enable AppArmor confinement with a
        custom profile.
    --apparmor.print=name|pid - print apparmor status.
    --appimage - sandbox an AppImage application.
    --bandwidth=name|pid - set bandwidth limits.
    --bind=dirname1,dirname2 - mount-bind dirname1 on top of dirname2.
    --bind=filename1,filename2 - mount-bind filename1 on top of filename2.
    --blacklist=filename - blacklist directory or file.
    --build - build a whitelisted profile for the application.
    --build=filename - build a whitelisted profile for the application.
    --caps - enable default Linux capabilities filter.
    --caps.drop=all - drop all capabilities.
    --caps.drop=capability,capability - blacklist capabilities filter.
    --caps.keep=capability,capability - whitelist capabilities filter.
    --caps.print=name|pid - print the caps filter.
    --cat=name|pid filename - print content of file from sandbox container.
    --chroot=dirname - chroot into directory.
    --cpu=cpu-number,cpu-number - set cpu affinity.
    --cpu.print=name|pid - print the cpus in use.
    --dbus-log=file - set DBus log file location.
    --dbus-system=filter|none - set system DBus access policy.
    --dbus-system.broadcast=rule - allow signals on the system DBus according
        to rule.
    --dbus-system.call=rule - allow calls on the system DBus according to rule.
    --dbus-system.log - turn on logging for the system DBus.
    --dbus-system.own=name - allow ownership of name on the system DBus.
    --dbus-system.see=name - allow seeing name on the system DBus.
    --dbus-system.talk=name - allow talking to name on the system DBus.
    --dbus-user=filter|none - set session DBus access policy.
    --dbus-user.broadcast=rule - allow signals on the session DBus according
        to rule.
    --dbus-user.call=rule - allow calls on the session DBus according to rule.
    --dbus-user.log - turn on logging for the user DBus.
    --dbus-user.own=name - allow ownership of name on the session DBus.
    --dbus-user.see=name - allow seeing name on the session DBus.
    --dbus-user.talk=name - allow talking to name on the session DBus.
    --debug - print sandbox debug messages.
    --debug-blacklists - debug blacklisting.
    --debug-caps - print all recognized capabilities.
    --debug-errnos - print all recognized error numbers.
    --debug-private-lib - debug for --private-lib option.
    --debug-protocols - print all recognized protocols.
    --debug-syscalls - print all recognized system calls.
    --debug-syscalls32 - print all recognized 32 bit system calls.
    --debug-whitelists - debug whitelisting.
    --defaultgw=address - configure default gateway.
    --deterministic-exit-code - always exit with first child's status code.
    --deterministic-shutdown - terminate orphan processes.
    --dns=address - set DNS server.
    --dns.print=name|pid - print DNS configuration.
    --dnstrace - monitor DNS queries.
    --env=name=value - set environment variable.
    --fs.print=name|pid - print the filesystem log.
    --get=name|pid filename - get a file from sandbox container.
    --help, -? - this help screen.
    --hostname=name - set sandbox hostname.
    --hosts-file=file - use file as /etc/hosts.
    --icmptrace - monitor Server Name Indiication (TLS/SNI).
    --ids-check - verify file system.
    --ids-init - initialize IDS database.
    --ignore=command - ignore command in profile files.
    --interface=name - move interface in sandbox.
    --ip=address - set interface IP address.
    --ip=none - no IP address and no default gateway are configured.
    --ip=dhcp - acquire IP address by running dhclient.
    --ip6=address - set interface IPv6 address.
    --ip6=dhcp - acquire IPv6 address by running dhclient.
    --iprange=address,address - configure an IP address in this range.
    --ipc-namespace - enable a new IPC namespace.
    --join=name|pid - join the sandbox.
    --join-filesystem=name|pid - join the mount namespace.
    --join-network=name|pid - join the network namespace.
    --join-or-start=name|pid - join the sandbox or start a new one.
    --keep-config-pulse - disable automatic ~/.config/pulse init.
    --keep-dev-shm - /dev/shm directory is untouched (even with --private-dev).
    --keep-fd - inherit open file descriptors to sandbox.
    --keep-var-tmp - /var/tmp directory is untouched.
    --list - list all sandboxes.
    --ls=name|pid dir_or_filename - list files in sandbox container.
    --mac=xx:xx:xx:xx:xx:xx - set interface MAC address.
    --machine-id - spoof /etc/machine-id with a random id
    --memory-deny-write-execute - seccomp filter to block attempts to create
        memory mappings that are both writable and executable.
    --mkdir=dirname - create a directory.
    --mkfile=filename - create a file.
    --mtu=number - set interface MTU.
    --name=name - set sandbox name.
    --net=bridgename - enable network namespaces and connect to this bridge.
    --net=ethernet_interface - enable network namespaces and connect to this
        Ethernet interface.
    --net=none - enable a new, unconnected network namespace.
    --net.print=name|pid - print network interface configuration.
    --netfilter[=filename,arg1,arg2,arg3 ...] - enable firewall.
    --netfilter.print=name|pid - print the firewall.
    --netfilter6=filename - enable IPv6 firewall.
    --netfilter6.print=name|pid - print the IPv6 firewall.
    --netlock - enable the network locking feature
    --netmask=address - define a network mask when dealing with unconfigured
        parent interfaces.
    --netns=name - Run the program in a named, persistent network namespace.
    --netstats - monitor network statistics.
    --nettrace - monitor received TCP, UDP and ICMP traffic.
    --nice=value - set nice value.
    --no3d - disable 3D hardware acceleration.
    --noblacklist=filename - disable blacklist for file or directory.
    --nodbus - disable D-Bus access.
    --nodvd - disable DVD and audio CD devices.
    --noexec=filename - remount the file or directory noexec nosuid and nodev.
    --nogroups - disable supplementary groups.
    --noinput - disable input devices.
    --nonewprivs - sets the NO_NEW_PRIVS prctl.
    --noprinters - disable printers.
    --noprofile - do not use a security profile.
    --noroot - install a user namespace with only the current user.
    --nosound - disable sound system.
    --noautopulse - disable automatic ~/.config/pulse init.
    --novideo - disable video devices.
    --nou2f - disable U2F devices.
    --nowhitelist=filename - disable whitelist for file or directory.
    --oom=value - configure OutOfMemory killer for the sandbox
    --output=logfile - stdout logging and log rotation.
    --output-stderr=logfile - stdout and stderr logging and log rotation.
    --private - temporary home directory.
    --private=directory - use directory as user home.
    --private-cache - temporary ~/.cache directory.
    --private-home=file,directory - build a new user home in a temporary
        filesystem, and copy the files and directories in the list in
        the new home.
    --private-bin=file,file - build a new /bin in a temporary filesystem,
        and copy the programs in the list.
    --private-dev - create a new /dev directory with a small number of
        common device files.
    --private-etc=file,directory - build a new /etc in a temporary
        filesystem, and copy the files and directories in the list.
    --private-tmp - mount a tmpfs on top of /tmp directory.
    --private-cwd - do not inherit working directory inside jail.
    --private-cwd=directory - set working directory inside jail.
    --private-opt=file,directory - build a new /opt in a temporary filesystem.
    --private-srv=file,directory - build a new /srv in a temporary filesystem.
    --profile=filename|profile_name - use a custom profile.
    --profile.print=name|pid - print the name of profile file.
    --protocol=protocol,protocol,protocol - enable protocol filter.
    --protocol.print=name|pid - print the protocol filter.
    --put=name|pid src-filename dest-filename - put a file in sandbox
        container.
    --quiet - turn off Firejail's output.
    --read-only=filename - set directory or file read-only.
    --read-write=filename - set directory or file read-write.
    --restrict-namespaces - seccomp filter that blocks attempts to create new namespaces.
    --restrict-namespaces=namespace,namespace - seccomp filter that blocks attempts
        to create specified namespaces.
    --rlimit-as=number - set the maximum size of the process's virtual memory.
        (address space) in bytes.
    --rlimit-cpu=number - set the maximum CPU time in seconds.
    --rlimit-fsize=number - set the maximum file size that can be created
        by a process.
    --rlimit-nofile=number - set the maximum number of files that can be
        opened by a process.
    --rlimit-nproc=number - set the maximum number of processes that can be
        created for the real user ID of the calling process.
    --rlimit-sigpending=number - set the maximum number of pending signals
        for a process.
    --rmenv=name - remove environment variable in the new sandbox.
    --scan - ARP-scan all the networks from inside a network namespace.
    --seccomp - enable seccomp filter and apply the default blacklist.
    --seccomp=syscall,syscall,syscall - enable seccomp filter, blacklist the
        default syscall list and the syscalls specified by the command.
    --seccomp.block-secondary - build only the native architecture filters.
    --seccomp.drop=syscall,syscall,syscall - enable seccomp filter, and
        blacklist the syscalls specified by the command.
    --seccomp.keep=syscall,syscall,syscall - enable seccomp filter, and
        whitelist the syscalls specified by the command.
    --seccomp.print=name|pid - print the seccomp filter for the sandbox
        identified by name or PID.
    --seccomp.32[.drop,.keep][=syscall] - like above but for 32 bit architecture.
    --seccomp-error-action=errno|kill|log - change error code, kill process
        or log the attempt.
    --shutdown=name|pid - shutdown the sandbox identified by name or PID.
    --tab - enable shell tab completion in sandboxes using private or
        whitelisted home directories.
    --timeout=hh:mm:ss - kill the sandbox automatically after the time
        has elapsed.
    --tmpfs=dirname - mount a tmpfs filesystem on directory dirname.
    --top - monitor the most CPU-intensive sandboxes.
    --trace - trace open, access and connect system calls.
    --tracelog - add a syslog message for every access to files or
        directories blacklisted by the security profile.
    --tree - print a tree of all sandboxed processes.
    --tunnel[=devname] - connect the sandbox to a tunnel created by
        firetunnel utility.
    --version - print program version and exit.
    --veth-name=name - use this name for the interface connected to the bridge.
    --whitelist=filename - whitelist directory or file.
    --writable-etc - /etc directory is mounted read-write.
    --writable-run-user - allow access to /run/user/$UID/systemd and
        /run/user/$UID/gnupg.
    --writable-var - /var directory is mounted read-write.
    --writable-var-log - use the real /var/log directory, not a clone.
    --x11 - enable X11 sandboxing. The software checks first if Xpra is
        installed, then it checks if Xephyr is installed. If all fails, it will
        attempt to use X11 security extension.
    --x11=none - disable access to X11 sockets.
    --x11=xephyr - enable Xephyr X11 server. The window size is 800x600.
    --x11=xorg - enable X11 security extension.
    --x11=xpra - enable Xpra X11 server.
    --x11=xvfb - enable Xvfb X11 server.
    --xephyr-screen=WIDTHxHEIGHT - set screen size for --x11=xephyr.
```










<br><br>
<br><br>
<br><br>
<br><br>

## Applications

<br><br>

## firefox (tested 2024)
- Download firefox https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-US and extract it to `/opt/firefox`

- We will use a temproy home folder with --private which means you can not save e.g. themes
  - This also means you can not install extension.
  - We also disabled sound. You amy want remove/change some args depending on your needs
```bash
firejail -private --noprofile --noprofile --disable-mnt --notv --caps.drop=all --private-cache --seccomp --private-cwd --private-tmp --nou2f --novideo --noautopulse --nosound --noroot --noprinters --nonewprivs --noinput --nogroups --nodvd --nodbus --no3d --name=firefoxSandbox --machine-id --dns=103.86.96.100 /opt/firefox/firefox
```

```
touch ~/Desktop/firefox-sandbox.desktop
sudo nano ~/Desktop/firefox-sandbox.desktop

#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Firefox [Sandboxed]
Exec=/bin/bash -c "firejail --noprofile --disable-mnt --notv --caps.drop=all --private-cache --seccomp --private-cwd --private-tmp --nou2f --novideo --noautopulse --nosound --noroot --noprinters --nonewprivs --noinput --nogroups --nodvd --nodbus --no3d --name=firefoxSandbox --machine-id --dns=103.86.96.100 /opt/firefox/firefox"
Type=Application
Terminal=true
Icon=/home/t33n/Documents/logos/firefox-logo.png
```

<br><br>
<br><br>

## google-chrome (Chrome and Chromium got for default seccomp)
- Not tested 2024
```bash
firejail --private-cache --nodbus --nogroups --caps.drop=all --noprofile --noroot --nou2f --notv --nodvd --noautopulse --no3d --disable-mnt --machine-id --nonewprivs --private-tmp --apparmor --dns=103.86.96.100 google-chrome
```


<br><br>
<br><br>

## spotify
- Not tested 2024
```bash
firejail --private-cache --nodbus --nogroups --caps.drop=all --noprofile --noroot --nou2f --notv --nodvd --noautopulse --no3d --disable-mnt --machine-id --seccomp --nonewprivs --apparmor --dns=103.86.96.100 --private-tmp spotify --disable-gpu --disable-software-rasterizer --no-zygote
```


<br><br>
<br><br>
-- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
<br><br>
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

# Profiles
- https://firejail.wordpress.com/features-3/man-firejail-profile/

## Autostart 
- **Notice that running the code below will at step 5 will enable firejail profiles for default. This means any application like e.g. firefox or chrome which has profiles will be started inside of firejail sandbox. This is maybe not what you want so it is more recommended to use the CLI instead and run specific applications in sandbox and create maybe desktop shortcuts**


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

5.
```bash
sudo firecfg
```
<br>6. At the next start the app will use your profile file.










<br><br>
<br><br>

## google-chrome.profile
- **Not tested 2024**
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
<br><br>
<br><br>




## spotify.profile
- **Not tested 2024**
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
- **Not tested 2024**
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
