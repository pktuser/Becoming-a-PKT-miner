This will work for WSL on Windows. I use this when I'm on vacation and worried about stupid windows updates or accidental overheat forcing restarts to my mining rigs.


## Step 1

create bash file `mineNow.sh` which is simply:

```
#!/bin/bash

while :

do

timeout 60 ~/packetcrypt ann -p pkt1qxrdhkc8ayyjtla97wmudpgvpz3w0y0tfa7lhfu http://pool.pkt.world/master/4096 http://pool.pktpool.io/ http://pool.pkteer.com/ 2>&1 | grep 'Ke/s'

done
```




set permissions to execute with `chmod +x mineNow.sh`

note: change to your wallet address




## Step 2

navigate to startup folder: %appdata%\Microsoft\Windows\Start Menu\Programs\Startup\

 - you want this in the startup folder so windows has access to it prior to any users logging in

create new .txt document file in the startup folder, type this into file: `wsl ~/mineNow.sh`

Save file as "all types" name it: `mineOnPowerOn.cmd`


## Step 3

Windows Task Scheduler:
create task scheduler task `minePKTonPowerOn`

Settings: 

- Run whether user is logged on or not
- Run with highest privileges
- Configure for Windows 10

triggers: At Startup, Delay task for 1 minute (this will give time for any background processes to load)

action: start a program, Program/script: navigate to `mineOnePowerOn.cmd` file and select that file, click OK.

- Change any other settings you want but this is the important stuff



Click ok, enter username and password of admin user to grant privileges to scheduled task.
