Trash
==

## Package Setup

    root@edison:~# nano /etc/opkg/base-feeds.conf
    src/gz all http://repo.opkg.net/edison/repo/all
    src/gz edison http://repo.opkg.net/edison/repo/edison
    src/gz core2-32 http://repo.opkg.net/edison/repo/core2-32
    root@edison:~# opkg update
    root@edison:~# opkg install nano git mpg123 python-pip python-opencv
    root@edison:~# pip install wolframalpha twython plotly paho-mqtt

## Workshop Setup

    root@edison:~# git clone https://github.com/xe1gyq/modules.git
    Cloning into 'modules'...
    remote: Counting objects: 495, done.
    remote: Compressing objects: 100% (50/50), done.
    remote: Total 495 (delta 24), reused 0 (delta 0), pack-reused 445
    Receiving objects: 100% (495/495), 45.89 KiB | 0 bytes/s, done.
    Resolving deltas: 100% (265/265), done.
    Checking connectivity... done.
    root@edison:~# cd modules
    root@edison:~/modules# git clone https://github.com/xe1gyq/core.git
    Cloning into 'core'...
    remote: Counting objects: 399, done.
    remote: Compressing objects: 100% (18/18), done.
    remote: Total 399 (delta 10), reused 0 (delta 0), pack-reused 381
    Receiving objects: 100% (399/399), 42.31 KiB | 0 bytes/s, done.
    Resolving deltas: 100% (245/245), done.
    Checking connectivity... done.
    root@edison:~/modules# cd core
    root@edison:~/modules/core# 
