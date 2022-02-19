

ks
-----

1,
ks相当于一台裸金属，网络只要能进DD就能识别，这里没有复杂的拓扑结构。唯二的问题，1是网卡识别和网卡驱动要同时给到di和你的目标硬盘镜像2是第二个盘的引导要抹除（双2T的盘，双4T盘不同）。

我记得ks1的网卡是河蟹卡，而ksle的是intel千兆卡。

2,
ksle的普通非中奖版是bios+mbr的。
而中奖版是uefi+gpt的（是仅uefi且强制uefi而不是uefi/legacy共存这种模式，但应该不强制gpt）。

分别需要找到对应且网卡驱动集好的正确镜像（而且因为ksle这种无vnc。如果是windows远程桌面必须开好）。

调试的时候最好用我的debug脚本。

3,
它有sys，ovh，和ks三个型号的产品和官网，其中有一种ovh子机

这个主机听说是独服开出来的，肯定不是自己装pve装esxi弄出来的，应该是ipmi开出来的，否则不会弄出这么复杂的网络结构：

表现也是在debianinstaller界面获取不到ip
另外，它的网关和ip不是同域的。这是常识了，其实一台机器可以有多个dns和多个gateway，但是路由上，只允许同时一个gateway出互联网，其它的gateway大概是做内网用的。

比如：54.39.xx.xx通过内网的192.168.2.7出网。这种

方法依然是ip命令一把梭


```
          ## ks
          #sudo sed -i "s/export[[:space:]]tmpBUILDGENE='0'/export tmpBUILDGENE='1'/g" ./ci.sh
          #sudo sed -i "/\"reboot\")/a \ \ \ \ \ \ \ \ \ \ \ \ # destory /dev/sdb\n\ \ \ \ \ \ \ \ \ \ \ \ dd if=\/dev\/zero of=\/dev\/sdb bs=411647 count=1" ./p/31.remaster/ci2.sh
          #sudo sed -i "/copy_including_deps[[:space:]]\$LMK\/kernel\/drivers\/net\/virtio_net.ko/a \ \ copy_including_deps \$LMK\/kernel\/drivers\/net\/ethernet\/intel\/igb\/igb.ko\n\ \ copy_including_deps \$LMK\/kernel\/drivers\/net\/ethernet\/intel\/e1000e\/e1000e.ko" ./p/31.remaster/ci2.sh
          #sudo sed -i "s/gitee.com\/minlearn\/onekeydevdesk/gitee.com\/minlearn\/onekeydevdeskks/g" ./ci.sh
          #sudo sed -i "s/github.com\/minlearn\/onekeydevdesk/github.com\/minlearn\/onekeydevdeskks/g" ./ci.sh
          #sudo sed -i "s/_build\/onekeydevdesk/_build\/onekeydevdeskks/g" ./ci.sh
          #sudo chmod +x ./ci.sh && sudo ./ci.sh -b 0 -h 0 -t onekeydevdesk
```
