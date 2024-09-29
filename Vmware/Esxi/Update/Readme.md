### Build numbers and versions of VMware ESXi/ESX
- https://knowledge.broadcom.com/external/article/316595/build-numbers-and-versions-of-vmware-esx.html
### how to upgrade
- https://www.ans.co.uk/docs/operatingsystems/vmware-esxi/upgrading-esxi/
- https://technet24.ir/%D8%A2%D9%85%D9%88%D8%B2%D8%B4-%D8%A8%D9%87-%D8%B1%D9%88%D8%B2-%D8%B1%D8%B3%D8%A7%D9%86%DB%8C-esxi-21419
- first download latest Bundle patch in .zip file . copy file in /tmp in vcentre appliance . 
```
esxcli software profile get
esxcli network firewall ruleset set -e true -r httpClient
Esxcli system maintenanceMode set –e true

esxcli software sources profile list -d /vmfs/volumes/’Name DATA STORE’/name_iso_upgrade.zip 
esxcli software profile update -d vmfs/volumes/’Name DATA STORE’/ iso_Offline Upgrade.zip -p ESXi-Version-standard.xml

Esxcli system maintenanceMode set –e false
esxcli software profile get
```
