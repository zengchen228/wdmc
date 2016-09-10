# Binary packages for WD My Cloud
## The is only for WD My Cloud with Firmware 4.x, not to Firmware 3.x or Firmware 2.x.

### Binary software list:
- aria2 - 1.26.1
- transmission - 2.92
- shadowsocks-libev - 2.5.0
- privoxy - 3.0.26
- ps3netsrv

### Install:
- Connect WDMC with ssh and execute the command below:

`tar zxvf opt-{version}.tar.gz -C /DataVolume`

### Start transmission, Please follow steps below: 
- step 1, start it one and kill it:

`/DataVolume/opt/bin/transmission-daemon -g /DataVolume/opt/var/.trsettings -t -r 0.0.0.0 -p 9091 -u <username> -v <password> -w /DataVolume/shares/Downloads`

`killall transmission-daemon`
  
- step 2, modfiy the settings.json in /DataVolume/opt/var/.trsettings, change rpc-whitelist value to '0.0.0.0':

.....
"rpc-whitelist-enabled": false,
.....
  
- step 3, start it , then you can start transmission with the lite-command:
`export TRANSMISSION_WEB_HOME=/DataVolume/opt/share/transmission/web`

`/DataVolume/opt/bin/transmission-daemon -g /DataVolume/opt/var/.trsettings`
  
- step 4: 
then you can access it with http://wdmycloude:9091.
