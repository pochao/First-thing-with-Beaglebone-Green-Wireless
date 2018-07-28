# 拿到開發板第一件要做的事

    Beaglebone開發板相對於Arduino、樹莓派是比較冷門
    當初會選擇BeagleBone Green Wireless是原因它基於Linux系統
    內建Wifi以及Cloud9開發環境，使用Node Js來做IoT相關項目是非常合適的

    拿到BBGW首先就是環境配置，到官網下載最新韌體，將韌體寫入micro SD
    再用micro SD開機就能更新韌體。更新完韌體，接下來是與電腦連線
    使用手機連到BBGW AP，自動進入wifi設定網頁，BBGW連上網路會得到一組IP
    電腦使用Chrome鍵入網址http://BBGW IP:3000，就能進入Cloud9開發環境

```linux
另一個設定wifi的方式,用電腦登入bbgw wifi,密碼BeagleBone (sudo密碼temppwd)
    sudo connmanctl technologies
    sudo connmanctl enable wifi
    sudo connmanctl services
    會列出可連線之wifi，記下wifi_2cf7f1062b04_5461626c652d322e3447_managed_psk
    sudo nano /var/lib/connman/Table-2.4G.config
    建立一個設定檔，內容如下
    [service_wifi_2cf7f1062b04_5461626c652d322e3447_managed_psk]
    Type = wifi
    Name = Table-2.4G
    Passphrase = My password
    存檔就會自動連線，可用sudo connmanctl technologies確認
```

```linux
啟用UART-2(內建grove cape)，在/boot/uEnv.txt加入cape_enable=bone_capemgr.enable_partno=BB-UART2
```

```linux
列出i2c裝置(BBGW內建為i2c-2) 
    i2cdetect -y -r 2
```

```linux
修改時區
    sudo dpkg-reconfigure tzdata
```

```linux
在Cloud9開啟終端機操作debian
更新Node版本至V6.x
    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
    sudo apt-get install -y nodejs
    sudo apt-get install -y build-essential
```

```linux
再重新安裝Cloud9
    sudo apt-get update 
    sudo apt-get install c9-core-installer --reinstall 
    sudo reboot
```

```linux
如果要更新系統套件使用
    sudo apt-get update
    sudo apt-get upgrade 
```

    注意:更新至Node V6.x會導致bonescript版本不符
    接下來就可以在Cloud9直接寫程式做項目了

```linux
遠端桌面連線方式
    vncserver -geometry 1280x800 :1
    使用vncviewer輸入192.168.7.2:5901
```
