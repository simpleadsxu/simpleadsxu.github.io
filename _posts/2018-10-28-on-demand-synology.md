---
layout: single
title:  "On Demand Synology"
date:   2020-04-18 12:0:0 -0400
author: JS
categories: NAS
tags:
  - Synology 
  - MacOs
excerpt: On demand synology for backup.
---

Unlike many people who leaves their NAS on 24/7, I only use it to backup my important data occassionally. Having the disks spnning all the time is just unncessary. So I decided to only turn it on when I need it.

I spent a few hours on a simple script, which semi-automated the process.


### Step 1, Wake-On-Lan
```bash
# WOL
read -n 1 -p "Is NAS offline, and WOL[Y/n]" wol
case $wol in
    [nN]*)
    echo "Ok. Assume it is online. Let's start backup" ;;

    *)
    echo "waking it up"
    wakeonlan [mac of your NAS]
    echo "wakeonlan sent. sleep for 5 minutes"
    sleep 300
    ;;
esac
```
Of course, we can skip it if your NAS is always online.

### Step 2, start Time Machine backup
```bash
# start time machine backup
tmutil startbackup
echo "Time machine backup started"
```
As you already guessed, I disabled automatically backup with Time Machine on my Mac. So this is just to turn it on.

### Step 3, run other backup
```bash
# mount drive
open afp://[nas shared folder]

[command to run other backup]
```
I don't trust Time Machine 100%, and would like to have the old-style backup, where I can see the actual icons on my files in NAS. You can use ``rsync`` or other software. 

Also, I spent a lot of time trying to automatically mount the NAS using ``smb`` or ``afp``. For whatever reason, it didn't play out well. Using ``open`` uses the default behavior as in ``Finder`` in MacOS. 

### Step 4, shutdown
Here, nothing is done yet. Ideally, I would like to receive ``finish`` signals from Time Machine and the other backup processes. 

Another challenge is  to shutdown  NAS remotely. I can do it via a SSH command with security key stored locally. 

But as you will guess, I am only doing it occasionally (weekly or  bi-weekly) for now. Guess I will live with this poor-man's solution for now.

TO DOs:
* Better auto mount
* Better finish signal
* Better shut-down control
