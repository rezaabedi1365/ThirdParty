#### Edit Zabbix config file in docker container
```
docker cp CONTAINER:/etc/zabbix/zabbix_server_vmware.conf .
```
umcomment this line 
```
StartVMwareCollectors=5
```
```
docker cp zabbix_server_vmware.conf CONTAINER:/etc/zabbix/zabbix_server_vmware.conf 
```

### 
```
docker restart CONTAINER
```

### Verify on host
```
ps aux | grep vmware
```
