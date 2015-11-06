Epicentro Festival 2015
==

## Pre-Requirements

- Laptop (Windows or Linux)
- USB Memory Stick

## Initial Considerations

Please...

- No Food or Drinks while you are working with the Intel Edison
- Edison + Arduino Breakout Board on top of anti-static bag

## Host Setup

- Do not connect your Itenl Edison yet

### Windows Based

Install in your Windows host, the Standalone Driver v1.2.1

- [Intel® Edison Board Software Downloads](https://software.intel.com/en-us/iot/hardware/edison/downloads)
- [Windows 64-bit Installer](http://downloadmirror.intel.com/25384/eng/w_iot_2015.0.028.exe)

Once installed, connect your Intel Edison using both USB cables, check in Device Manager, under **Ports (COM & LPT)** which port your Edison has been assigned with the label

In Windows

    ipconfig/release
    ipconfig/renew

- USB Serial Port (COMxx)

### Linux Based

You should have everything ready, type

    $ dmesg

and find out at the end of the out put stream which tty your Edison has been assigned to, it should be **/dev/ttyUSB0**

## Core Code Repository

- [Core Gitbook](https://xe1gyq.gitbooks.io/core/content/)

## Logging In

Version 1.6

    Poky (Yocto Project Reference Distro) 1.6 edison ttyMFD2
    ...
    edison login: root
    root@edison:~# 

Version 1.7

    Poky (Yocto Project Reference Distro) 1.7.2 edison ttyMFD2
    ...
    edison login: root
    root@edison:~#

## Internet Configuration

    root@edison:~# ifconfig usb0 down
    root@edison:~# configure_edison --wifi
    root@edison:~# ifconfig
    ...
    wlan0     Link encap:Ethernet  HWaddr 78:4b:87:a7:e0:19  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
    ...
    root@edison:~# ping -c 2 google.com
    PING google.com (74.125.28.100): 56 data bytes
    64 bytes from 74.125.28.100: seq=0 ttl=41 time=99.709 ms
    64 bytes from 74.125.28.100: seq=1 ttl=41 time=113.055 ms

    --- google.com ping statistics ---
    2 packets transmitted, 2 packets received, 0% packet loss
    round-trip min/avg/max = 99.709/106.382/113.055 ms
    root@edison:~# 

## Getting Started

    root@edison:~# cd
    root@edison:~# ls
    modules
    root@edison:~# cd modules/core/
    root@edison:~/modules/core# ls
    LICENSE                svoicerss.sh           xspeechrecognition.py
    README.md              xanswer.py             xtalk.py
    SUMMARY.md             xcamera.py             xtweet.py
    __init__.py            xfacerecognition.py    xvoice.py
    configuration          xlcdrgb.py             xwolfram.py
    documentation          xmqttpub.py
    output                 xplotly.py
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

In your browser go to www.wolframalpha.com and find out about this site
Run xwolframpy script

    root@edison:~/modules/core# python xwolfram.py
    Mexico City Distrito Federal Mexico

[Code xWolfram](https://github.com/xe1gyq/core/blob/master/xwolfram.py)

### Practice

Now modify the code to ask a different question to WolframAlpha

    root@edison:~/modules/core# nano xwolfram.py
       <Modify Code>
      <CTRL-X to Save>
    root@edison:~/modules/core# python xwolfram.py

## Twitter

Run xtweet script

    root@edison:~/modules/core# python xtweet.py
    /usr/lib/python2.7/site-packages/requests/packages/urllib3/util/ssl_.py:100: InsecurePlatformWarning: A true SSLContext o.
      InsecurePlatformWarning
    root@edison:~/modules/core# nano xtweet.py

[Code xtweet](https://github.com/xe1gyq/core/blob/master/xtweet.py)

### Practice

Send 1 tweet mentioning @EpicentroFes + hashtag #EpicentroFest + the names of team members

## Face Recognition

    root@edison:~/modules/core# time python xfacerecognition.py
    Found 17 faces!

[Code xFaceRecognition](https://github.com/xe1gyq/core/blob/master/xfacerecognition.py)

### Practice

Download a jpeg image with one or more human faces from the internet to your Intel Edison, rename it as in.jpeg and run face recognition script again, the steps are

    root@edison:~/modules/core# cd output
    root@edison:~/modules/core/output# ls
    in.jpeg   out.jpeg
    root@edison:~/modules/core/output# wget <jpeg image url>
    root@edison:~/modules/core/output# ls
    in.jpeg   out.jpeg   imagename.weirdname
    root@edison:~/modules/core/output# mv imagename.weirdname in.jpeg
    root@edison:~/modules/core/output# cd ..
    root@edison:~/modules/core# python xfacerecognition.py
    root@edison:~/modules/core# cp output/out.jpeg /usr/lib/edison_config_tools/public
    root@edison:~/modules/core# ifconfig
    ...
    wlan0     Link encap:Ethernet  HWaddr 78:4b:87:a7:e0:19  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
    ...
    Open your browser and go to url:
    <ip>/out.jpeg
    192.168.1.70/out.jpeg

## Plot.Ly

    root@edison:~/modules/core# python xplotly.py
    /usr/lib/python2.7/site-packages/requests/packages/urllib3/util/ssl_.py:100: InsecurePlatformWarning: A true SSLContext o.
      InsecurePlatformWarning
    /usr/lib/python2.7/site-packages/requests/packages/urllib3/util/ssl_.py:100: InsecurePlatformWarning:
    A true SSLContext object is not available. This prevents urllib3 from configuring SSL appropriately and may cause certain.

[Code xPlotLy](https://github.com/xe1gyq/core/blob/master/xplotly.py)

### Practice

Modify the code to graph a random number between 0 and 99

[Generate random integers between 0 and 9](http://stackoverflow.com/questions/3996904/generate-random-integers-between-0-and-9)

## MQTT
    
    root@edison:~/modules/core# cd
    root@edison:~# mosquitto_sub -h test.mosquitto.org -p 1883 -t theiotlearninginitiative/workshop
    root@edison:~# mosquitto_pub -h test.mosquitto.org -p 1883 -t theiotlearninginitiative/workshop -m "Hello Mqtt!"
    root@edison:~# mosquitto_sub -h test.mosquitto.org -t "#" -v

## Shutdown

    root@edison:~# cd
    root@edison:~# rm -rf modules/
    root@edison:~# poweroff

