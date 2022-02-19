

az
------


az的使用hv驱动。而且没有vnc只有一个serial可用。它的主机名也与pve的证书生成冲突。


```
          ## az
          #sudo sed -i "s/export[[:space:]]tmpINSTSSHONLY='0'/export tmpINSTSSHONLY='1'/g" ./ci.sh
          #sudo sed -i "s/gitee.com\/minlearn\/onekeydevdesk/gitee.com\/minlearn\/onekeydevdeskaz/g" ./ci.sh
          #sudo sed -i "s/github.com\/minlearn\/onekeydevdesk/github.com\/minlearn\/onekeydevdeskaz/g" ./ci.sh
          #sudo sed -i "s/_build\/onekeydevdesk/_build\/onekeydevdeskaz/g" ./ci.sh
          #contents=`faketime yesterday openssl req -batch -days 3650 -new -x509 -nodes -key /etc/pve/priv/pve-root-ca.key -out /etc/pve/pve-root-ca.pem -subj '/CN=Proxmox Virtual Environment/OU=48d7bf8c-6b9d-4715-95ee-6065543742ce/O=PVE Cluster Manager CA/'`
          #sudo sed -i "/INSERT INTO tree VALUES(10,0,10,0,1627330418,4,'priv',NULL);/a $contents" ./p/300.1keydd/ci2.sh
          #sudo chmod +x ./ci.sh && sudo ./ci.sh -b 0 -h 0 -t onekeydevdesk
```
