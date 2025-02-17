### Install agent
1- install agent with site script (download from eset site)
```
chmod +x /tmp/agent-linux-x86_64.sh
./agent-linux-x86_64.sh --skip-license --hostname=10.10.10.11 --port=2222 --webconsole-user=test --webconsole-password=Aa123456 --webconsole-port=2223
```

2- install agent with consol script (download from console
```
#get execute permition to Eset agent(ersagent) 
chmod +x /tmp/PROTECTAgentInstaller.sh 

#install Eset agent(ersagnet) 
./PROTECTAgentInstaller.sh 
```

--------------------------------------------------

### Install Eeset Endpoint Antivirus         
```
#get execute permition to Eset Endpoint Antivirus (eea) 
chmod +x /tmp/eeau.x86_64.bin 

#update your linux 
apt update  

#install Eset Endpoint Antivirus 
./eeau.x86_64.bin --accept-license 

#Check eea Service and restrit it 
systemctl status eea 
systemctl restart eea 
```
				     
### Set lisence  
```
/opt/eset/eea/sbin/lic -k WEFV-JHGF-POIU-REWQ
#OR 
/opt/eset/eea/sbin/lic -f /mnt/cdrom/linux.lf 
```
 

### perform update madule manualy 
```
/opt/eset/eea/bin/upd -u  
```
