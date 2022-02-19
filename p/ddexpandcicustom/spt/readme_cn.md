
spt
-----

spt是一台普通难度的机器，唯一的挑战是没有挑战。要说有，就是镜像要找到一个小于15g的


```
          ## spt15g
          #sudo sed -i "s/export[[:space:]]custIMGSIZE='20'/export custIMGSIZE='15'/g" ./ci.sh
          #sudo sed -i "s/imgsizeinfo=\$TARGETDDIMGSIZE/imgsizeinfo='15'/g" ./p/31.remaster/ci2.sh
          #sudo sed -i "s/gitee.com\/minlearn\/onekeydevdesk/gitee.com\/minlearn\/onekeydevdeskspt15g/g" ./ci.sh
          #sudo sed -i "s/github.com\/minlearn\/onekeydevdesk/github.com\/minlearn\/onekeydevdeskspt15g/g" ./ci.sh
          #sudo sed -i "s/_build\/onekeydevdesk/_build\/onekeydevdeskspt15g/g" ./ci.sh
          #sudo chmod +x ./ci.sh && sudo ./ci.sh -b 0 -h 0 -t onekeydevdesk
```

