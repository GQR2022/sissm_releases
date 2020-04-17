# sissm_releases

Simple Insurgency Sandstorm Server Manager - SISSM
Quick Start Guide for SISSM
JS Schroeder -- last updated:  2019.09.05
===============================

For source, description and documentation of SISSM, visit:
https://github.com/schroeder-lvb/sissm

This is a quick-start install instruction site for SISSM, if --
*  You are using pre-compiled executable package (Windows/Debian9/Ubuntu18)
*  You already have a working Co-op mode Insurgency Sandstorm Server, and
*  You have full control of your server (shell access) for installing 3rd party software,
   e.g., home server or cloud-based VPS (but not a commercial game hosting service)

---------------------------------
Step 1: Your Existing Server
---------------------------------

A) Game.ini -- Make sure RCON is enabled, for example:

```
[Rcon]
bEnabled=True
Password=mysecretpassword
ListenPort=27015
```
B) Your Game Server launcher script -- Make sure logging is enabled

Linux -
```./InsurgencyServer-Linux-Shipping [ ...your params... ] -log -LogCmds="LogGameplayEvents Log"```

Windows -
```InsurgencyServer-Win64-Shipping [ ...your params... ] -log -LogCmds="LogGameplayEvents Log"```

NOTE: If you are hosting multiple server instances *FROM THE SAME INSTALL FOLDER* you
must specify unique log file for each.  Do this by changing "-log" with e.g., "-log=server1.log",
creating s server1.log file instead of Insurgency.log.  This applies to "Sandstorm Admin
Wrapper (SAW)" users hosting more than one instance of the game.


---------------------------------
Step 2: Download the Quick Install .zip file to your server
---------------------------------

https://github.com/schroeder-lvb/sissm_releases

Download the latest 'quick-start' package and unzip to an empty folder:

*  sissm                  Linux executable
*  sissm_restricted       Linux variant for GSPs - script execution is disabled for security
*  sissm.exe              Windows executable
*  sissm_restricted.exe   Windows variant for GSPs - script execution is disabled for security
*  sissm_example.cfg    Starter configuration (from which you will make a copy and edit)

(There may be 32- and 64-bit versions of the Windows executable.)

SISSM must run on the same machine alongside your game server, with read access to
the game log (Insurgency.log) and Admins.txt files.

First time: make your custom sissm.cfg by copying from the sisssm_example.cfg file.
If you have multiple game instances on the same server you might name them as
sissm1.cfg, sissm2.cfg, etc.

---------------------------------
Step 3:  Edit your sissm.cfg file
---------------------------------

Edit sissm.cfg, find and update four variables at top.  "//" are comments.

Linux example -- REPLACE WITH YOUR OWN:
```
sissm.RconPort           27015
sissm.RconPassword       "mysecretpassword"
sissm.rootguids          "76560000000000001"      // your SteamID ("root user")
sissm.GameLogFile        "/home/ins/iss/Insurgency/Saved/Logs/Insurgency.log"
```
Windows example -- REPLACE WITH YOUR OWN:
```
sissm.RconPort           27015
sissm.RconPassword       "mysecretpassword"
sissm.rootguids          "76560000000000001"      // your SteamID ("root user")
sissm.GameLogFile        "C:\Program Files (x86)\Steam\steamapps\common\sandstorm_server\Insurgency\Saved\Logs\Insurgency.log"
```

---------------------------------
Step 4:  Run it
---------------------------------

a)  Start your Insurgency Server

b)  Start SISSM

Linux (bash):
```
    cd [your folder]
    chmod +x sissm
    ./sissm sissm.cfg
```

Windows command shell
```
    cd [your folder]
    sissm sissm.cfg (DOS shell) or ./sissm.exe sissm.cfg (PowerShell)
```

Windows for keybaord-challenged people:
```
    Put sissm.exe and sissm.cfg in the same folder
    Rename sissm.cfg to sissm_default.cfg
    Double click on sissm.exe
```

c)  Control-C to stop SISSM.

---------------------------------
Step 5:  Customize Your SISSM.CFG file
---------------------------------

SISSM comes with many powerful plugins.  Walk through your sissm.cfg file and
customize it for your own needs.

Consult individual plugin documentations on how to setup various features.
Note some plugins are disabled by default on the distribution package.

Almost all of SISSM's messages sent to the game clients are defined in the SISSM.CFG file.
Experiment with language localization according to your server location.

