# No More Room in Hell Server Setup Guide
This guild is trying to show how to setup up an No More Roon in Hell dedicated server under Linux environment. <br/>
This guid is well tested on Ubuntu 18.04 LTS. <br/>

## 1. Hardware Requirement
The following spec is good enought to host a full-team (8 ppl) server: 
* 1 CPU core
* 1 GB Ram
* ~8 GB hard disk

also, please remember opening the port 27015 on your firewall before we go.

## 2. Step up on Linux Environment
To host NMRiH server on a Linux machine, please do the following step by step -

### 2.1 Download Server file via SteamCmd
download SteamCmd firstly: <br>
(in here , we assume using the path `~/Steam`)

``` shell
cd ~/SteamCMD
wget http://media.steampowered.com/installer/steamcmd_linux.tar.gz 
tar xvfz steamcmd_linux.tar.gz
```

run SteamCMD so as to download NMRiH Server file:

``` shell
./steamcmd.sh
```
``` shell
login anonymous 
force_install_dir ./NMRiHServer/
......
app_update 317670 validate
(will donwload 7G file)	
......
quit
```

### 2.2 Download Server Package
to mske the NMRiH can run under a 64-bit machine, we are goingto install:
``` shell
apt-get install lib32gcc1
```

### 2.3 Set Config
please edit the following config before you kick the server:
``` shell
cd ~/SteamCmd/NMRiNServer/nmrih/cfg
vi server.cfg
```
Optionally, you can edit the server message:
``` shell
(optional)
cd ~/SteamCmd/NMRiNServer/nmrih/cfg
vi motd_default.txt
```
Optionally, you can edit the map cycle:
``` shell
(optional)
cd ~/SteamCmd/NMRiNServer/nmrih/cfg
vi mapcycle.txt
```

### 2.4 Linking Missing File List 
due to a bug under the current version, we have to link the following file name:
``` shell
cd ~/SteamCmd/NMRiNServer/bin
ln -s scenefilecache_srv.so scenefilecache.so
ln -s soundemittersystem_srv.so soundemittersystem.so
```

### 2.5 Kick Server
We create a script to kick the server:

``` shell
cd ~/SteamCmd/NMRiNServer
touch start.sh
chmod 744 start.sh
vi start.sh
```
(please change the path, ip, port, player no. and startig map, according to your environment)
```xml
./srcds_run -game nmrih -maxplayers 8 +map nmo_boardwalk -ip xxx.xxx.xxx -port yyyyy(e.g. 27015)
```
run the server by entering the following command:
``` shell
cd ~/SteamCmd/NMRiNServer
./start.sh
```

then make sure the server is running and no error occurred.

ENJOY!

:100:

