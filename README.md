# 第一件事 Beaglebone Green Wireless

    Beaglebone開發板相對於Arduino、樹莓派是比較冷門
    當初會選擇BeagleBone Green Wireless是原因它基於Linux系統
    內建Wifi以及Cloud9開發環境，使用Node Js來做IoT相關項目是非常合適的

    拿到BBGW首先就是環境配置，到官網下載最新韌體，將韌體寫入micro SD
    再用micro SD開機就能更新韌體。更新完韌體，接下來是與電腦連線
    使用手機連到BBGW AP，自動進入wifi設定網頁，BBGW連上網路會得到一組IP
    電腦使用Chrome鍵入網址http://BBGW IP:3000，就能進入Cloud9開發環境

    在Cloud9開啟終端機操作debian

    更新Node版本至V6.x
    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
    sudo apt-get install -y nodejs

    sudo apt-get install -y build-essential

    在重新安裝Cloud9
    sudo apt-get update 
    sudo apt-get install c9-core-installer --reinstall 
    sudo reboot

    如果要更新系統套件使用
    sudo apt-get update
    sudo apt-get upgrade 

注意:更新至Node V6.x會導致bonescript版本不符

接下來就可以在Cloud9直接寫程式做項目了
