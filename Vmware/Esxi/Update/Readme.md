### Build numbers and versions of VMware ESXi/ESX
- https://knowledge.broadcom.com/external/article/316595/build-numbers-and-versions-of-vmware-esx.html
### how to upgrade
- https://www.ans.co.uk/docs/operatingsystems/vmware-esxi/upgrading-esxi/
- https://technet24.ir/%D8%A2%D9%85%D9%88%D8%B2%D8%B4-%D8%A8%D9%87-%D8%B1%D9%88%D8%B2-%D8%B1%D8%B3%D8%A7%D9%86%DB%8C-esxi-21419
- first download latest Bundle patch in .zip file . copy file in /tmp in vcentre appliance .

show current version
```
vmware -v
esxcli system version get
```
Enable MaitenanceMode
```
esxcli system maintenanceMode set -e true
vim-cmd hostsvc/maintenance_mode_enter
#verify:
esxcli system maintenanceMode get
```
 List of update 
- copy file in to das
- find your storage id
- list of update in your file
```
esxcli software sources profile list --depot=file:///vmfs/volumes/6476fd67-83fa22cb-7ac6-e4115baac5c4/ESXi600-202002001.zip
#--depot=file:  =  -d
```
 example
```
Name                             Vendor        Acceptance Level
-------------------------------  ------------  ----------------
ESXi-6.0.0-20200204001-standard  VMware, Inc.  PartnerSupported
ESXi-6.0.0-20200204001-no-tools  VMware, Inc.  PartnerSupported
```
install update :
```
esxcli software profile update --depot=file:///vmfs/volumes/6476fd67-83fa22cb-7ac6-e4115baac5c4/ESXi600-202002001.zip -p ESXi-6.0.0-20200204001-standard
```
Update Result
   - Message: The update completed successfully, but the system needs to be rebooted for the changes to be
   - effective.
            *  Reboot Required: true

  
-------------------------------------------------------------------------------------------------------------------------------

```
esxcli software profile get
esxcli network firewall ruleset set -e true -r httpClient
Esxcli system maintenanceMode set –e true

esxcli software sources profile list -d /vmfs/volumes/’Name DATA STORE’/name_iso_upgrade.zip 
esxcli software profile update -d vmfs/volumes/’Name DATA STORE’/ iso_Offline Upgrade.zip -p ESXi-Version-standard.xml

Esxcli system maintenanceMode set –e false
esxcli software profile get
```
