### Linux
```
curl -so wazuh-agent-4.3.10.deb http://10.10.10.11:3333/wazuh-agent_4.3.10-1_amd64.deb \
&& sudo WAZUH_MANAGER='10.10.11.12' WAZUH_AGENT_GROUP='default' dpkg -i ./wazuh-agent-4.3.10.deb
```
```
sudo systemctl daemon-reload
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```
### Windows
```
Invoke-WebRequest -Uri http://10.10.10.11:3333/wazuh-agent-4.3.10-1.msi -OutFile ${env:tmp}\wazuh-agent-4.3.10.msi;msiexec.exe /i ${env:tmp}\wazuh-agent-4.3.10.msi /q WAZUH_MANAGER='10.10.10.12' WAZUH_REGISTRATION_SERVER='10.10.10.12' WAZUH_AGENT_GROUP='default'

NET START wazuh
```
