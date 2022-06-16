This will work for WSL on Windows. I use this when I'm on vacation and worried about stupid windows updates or accidental overheat forcing restarts to my mining rigs.

create bash file `mineNow.sh` which is simply:
`../packetcrypt ann -p pkt1qxrdhkc8ayyjtla97wmudpgvpz3w0y0tfa7lhfu http://pool.pkt.world/master/4096 http://pool.pktpool.io/ http://pool.pkteer.com/`



create `mineOnPowerUp.cmd` file in the startup folder
%appdata%\Microsoft\Windows\Start Menu\Programs\Startup\
mineOnPowerUp.cmd code to be: `wsl ~/mineNow.sh`
 - you want this in the startup folder so windows has access to it prior to any users logging in



Windows Task Scheduler:
create task scheduler task "minePKTonPowerOn"
- Run whether user is logged on or not
- Run with highest privileges
- Configure for Windows 10
triggers: At Startup, Delay task for 1 minute (this will give time for any background prcesses to get loaded)
action: start a program, Program/script: navigate to `mineOnePowerUp.cmd` file and select that file, click OK.
- Change any other settings you want but this is the important stuff



Click ok, enter username and password of admin user to grant privileges to scheduled task.
