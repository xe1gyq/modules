Epicentro Festival 2015
==

## Initial Considerations

- No food or drinks while you are working with the board
- Edison + Arduino Breakout Board on top of anti-static bag


## Logging In

    Poky (Yocto Project Reference Distro) 1.6 edison ttyMFD2

    edison login: root
    root@edison:~# 


## Internet Configuration

    root@edison:~# configure_edison --wifi
    root@edison:~# ifconfig
    ...
    wlan0     Link encap:Ethernet  HWaddr 78:4b:87:a7:e0:19  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
    ...

## Package Setup

    root@edison:~# vi /etc/opkg/base-feeds.conf
    src/gz all http://repo.opkg.net/edison/repo/all
    src/gz edison http://repo.opkg.net/edison/repo/edison
    src/gz core2-32 http://repo.opkg.net/edison/repo/core2-32
    root@edison:~# opkg update
    root@edison:~# opkg install nano git mpg123 python-pip python-opencv fswebcam
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

## Credentials

    root@edison:~/modules/core# nano configuration/credentials.config
    [wolfram]
    appid = 
    
    [twitter]
    consumer_key = 
    consumer_secret = 
    access_token = 
    access_token_secret = 
    
    [plotly]
    username = TheIoTLearningInitiative
    apikey = 
    streamtoken = 

## WolframAlpha

    root@edison:~/modules/core# python xwolfram.py
    Mexico City Distrito Federal Mexico

### Practice

Ask 2 different questions to WolframAlpha

    root@edison:~/modules/core# nano xwolfram.py

## Twitter
    
    root@edison:~/modules/core# python xtweet.py
    /usr/lib/python2.7/site-packages/requests/packages/urllib3/util/ssl_.py:100: InsecurePlatformWarning: A true SSLContext o.
      InsecurePlatformWarning
    root@edison:~/modules/core# nano xtweet.py

### Practice

Send 1 tweet mentioning @EpicentroFes with hashtag #EpicentroFest with all the names of team members

## Face Recognition

    root@edison:~/modules/core# python xfacerecognition.py
    Found 17 faces!

### Practice

Get a jpeg image with one or more human faces from the internet, rename it as in.jpeg and run face recognition script

    root@edison:~/modules/core# cd output
    root@edison:~/modules/core/output# ls
    in.jpeg   out.jpeg
    root@edison:~/modules/core/output# wget <jpeg image url>
    root@edison:~/modules/core/output# ls
    in.jpeg   out.jpeg   imagename.weirdname
    root@edison:~/modules/core/output# mv imagename.weirdname in.jpeg
    root@edison:~/modules/core/output# cd ..
    root@edison:~/modules/core# python xfacerecognition.py

## Plot.Ly

    root@edison:~/modules/core# python xplotly.py
    /usr/lib/python2.7/site-packages/requests/packages/urllib3/util/ssl_.py:100: InsecurePlatformWarning: A true SSLContext o.
      InsecurePlatformWarning
    /usr/lib/python2.7/site-packages/requests/packages/urllib3/util/ssl_.py:100: InsecurePlatformWarning:
    A true SSLContext object is not available. This prevents urllib3 from configuring SSL appropriately and may cause certain.

### Practice

Continously graph a random number between 0 and 99

[Generate random integers between 0 and 9](http://stackoverflow.com/questions/3996904/generate-random-integers-between-0-and-9)

## MQTT
    
    root@edison:~/modules/core# cd
    root@edison:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t theiotlearninginitiative/workshop
    root@edison:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t theiotlearninginitiative/workshop "Hello Mqtt!"
    root@edison:~# mosquitto_sub -h test.mosquitto.org -t "#" -v



