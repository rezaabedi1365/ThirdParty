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
dpkg -i <packge name>
mkdir -p /opt/splunkforwarder/etc/system/local
echo "[target-broker:deploymentServer]" > /opt/splunkforwarder/etc/system/local/deploymentclient.conf
echo "targetUri = 172.22.68.11:8089" >> /opt/splunkforwarder/etc/system/local/deploymentclient.conf
/opt/splunkforwarder/bin/splunk restart
```
