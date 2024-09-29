### Build numbers and versions of VMware ESXi/ESX
- https://knowledge.broadcom.com/external/article/316595/build-numbers-and-versions-of-vmware-esx.html
### how to upgrade
https://technet24.ir/%D8%A2%D9%85%D9%88%D8%B2%D8%B4-%D8%A8%D9%87-%D8%B1%D9%88%D8%B2-%D8%B1%D8%B3%D8%A7%D9%86%DB%8C-esxi-21419
- first download latest Bundle patch in .zip file . copy file in /tmp in vcentre appliance . 
```
esxcli software profile get
esxcli network firewall ruleset set -e true -r httpClient

esxcli software sources profile list -d https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml  | grep -i ESXi-6
esxcli software profile update -p PACKAGE-NAME -d https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml

esxcli software profile get
```
