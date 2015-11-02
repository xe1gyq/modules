Modules
==

Getting Started

    root@edison:~# configure_edison --wifi
    root@edison:~# ifconfig
    ...
    wlan0     Link encap:Ethernet  HWaddr 78:4b:87:a7:e0:19  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
    ...
    root@edison:~# vi /etc/opkg/base-feeds.conf
    src/gz all http://repo.opkg.net/edison/repo/all
    src/gz edison http://repo.opkg.net/edison/repo/edison
    src/gz core2-32 http://repo.opkg.net/edison/repo/core2-32
    root@edison:~# opkg update
    root@edison:~# opkg install git mpg123 python-pip nano
    root@edison:~# pip install wolframalpha
    root@edison:~# git clone --recursive https://github.com/xe1gyq/modules.git
    Cloning into 'modules'...
    remote: Counting objects: 43, done.
    remote: Compressing objects: 100% (42/42), done.
    remote: Total 43 (delta 22), reused 2 (delta 0), pack-reused 0
    Unpacking objects: 100% (43/43), done.
    Checking connectivity... done.
    git: 'submodule' is not a git command. See 'git --help'.
    root@edison:~# cd modules
    root@edison:~# rmdir core
    root@edison:~/modules# git clone https://github.com/xe1gyq/core.git
    Cloning into 'core'...
    remote: Counting objects: 399, done.
    remote: Compressing objects: 100% (18/18), done.
    remote: Total 399 (delta 10), reused 0 (delta 0), pack-reused 381
    Receiving objects: 100% (399/399), 42.31 KiB | 0 bytes/s, done.
    Resolving deltas: 100% (245/245), done.
    Checking connectivity... done.
    

    

