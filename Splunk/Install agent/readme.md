
# Linux 
### Method1
- use splunk command to config
- you need to admin password
```
dpkg -i <packge name> 
/opt/splunkforwarder/bin/splunk start
/opt/splunkforwarder/bin/splunk enable boot-start
/opt/splunkforwarder/bin/splunk set deploy-poll 10.10.10.11:8089
/opt/splunkforwarder/bin/splunk restart
```
### Method2
- without Splunk commnand and with change config file 
- in this method you dont need to admin password
```
chmod +x splunkforwarder-9.2.2-amd64.deb
dpkg -i splunkforwarder-9.2.2-amd64.deb 
sudo /opt/splunkforwarder/bin/splunk enable boot-start -user splunkfwd --accept-license --answer-yes --no-prompt --gen-and-print-passwd
mkdir -p /opt/splunkforwarder/etc/system/local
echo "[target-broker:deploymentServer]" > /opt/splunkforwarder/etc/system/local/deploymentclient.conf
echo "targetUri = 10.10.10.11:8089" >> /opt/splunkforwarder/etc/system/local/deploymentclient.conf
sudo chown splunkfwd:splunkfwd /opt/splunkforwarder/etc/system/local/deploymentclient.conf
/opt/splunkforwarder/bin/splunk restart
```
### verity
```
nano /opt/splunkforwarder/etc/system/local/server.conf
```

### Unistall
```
sudo /opt/splunkforwarder/bin/splunk stop
sudo /opt/splunkforwarder/bin/splunk disable boot-start
sudo apt purge splunkforwarder
sudo rm -rf /opt/splunkforwarder
```
# Windows
```
Invoke-WebRequest -Uri http://10.10.10.11:3333/splunkuf.msi -OutFile ${env:tmp}\splunkuf.msi
msiexec.exe /i ${env:tmp}\splunkuf.msi AGREETOLICENSE=Yes DEPLOYMENT_SERVER="10.10.10.12:8089" SPLUNKUSERNAME=uf-admin GENRANDOMPASSWORD=1 /quiet  
```
-----------------------------------------------------------------------------------------------------------------------------
### Reset Setting
```
sudo /opt/splunkforwarder/bin/splunk stop
sudo /opt/splunkforwarder/bin/splunk clone-prep-clear-config
sudo /opt/splunkforwarder/bin/splunk enable
sudo /opt/splunkforwarder/bin/splunk restart
```
