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
```
tar zxvf opt-{version}.tar.gz -C /DataVolume
```

### Start transmission, Please follow steps below: 
- step 1, start it one and kill it:
```
/DataVolume/opt/bin/transmission-daemon -g /DataVolume/opt/var/.trsettings -t -r 0.0.0.0 -p 9091 -u <username> -v <password> -w /DataVolume/shares/Downloads
killall transmission-daemon
```

- step 2, modfiy the settings.json in /DataVolume/opt/var/.trsettings, change rpc-whitelist value to '0.0.0.0':
```
.....
"rpc-whitelist-enabled": false,
.....
```

- step 3, start it , then you can start transmission with the lite-command:
```
export TRANSMISSION_WEB_HOME=/DataVolume/opt/share/transmission/web
/DataVolume/opt/bin/transmission-daemon -g /DataVolume/opt/var/.trsettings
```

- step 4: 
then you can access it with http://wdmycloude:9091.

### Start aria2, please follow the steps below:
- step 1, create the /DataVolume/opt/etc/aria2.conf , there is a aria2.conf sample below:
```
daemon=true
enable-rpc=true
rpc-allow-origin-all=true
rpc-listen-all=true
rpc-listen-port=6800
rpc-secret=7ac9aa62-8a9c-4724-83f2-e84f32f3f7ee

max-concurrent-downloads=5
continue=true
max-connection-per-server=5
min-split-size=10M
split=10

input-file=/DataVolume/opt/var/.aria2/aria2.session
save-session=/DataVolume/opt/var/.aria2/aria2.session
save-session-interval=60

dir=/DataVolume/shares/Downloads
file-allocation=prealloc

enable-dht=false
bt-enable-lpd=false
enable-peer-exchange=false
user-agent=uTorrent/2210(25130)
peer-id-prefix=-UT2210-
seed-ratio=0
force-save=true
bt-hash-check-seed=true
bt-seed-unverified=true
bt-save-metadata=true

ca-certificate=/DataVolume/opt/share/curl/ca-bundle.crt
```

- step 2, create the session and downloads dir, and session file:
```
mkdir /DataVolume/opt/var/.aria2
mkdir /DataVolume/shares/Downloads
touch /DataVolume/opt/var/.aria2/aria2.session
```

- step 3, start aria2 with the command below:
```
/DataVolume/opt/bin/aria2c --conf-path=/DataVolume/opt/etc/aria2.conf
```

- step 4, enjoy it
