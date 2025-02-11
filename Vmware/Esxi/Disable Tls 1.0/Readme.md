Bahmani
### Disable TLS Versions on Vcenter
https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-BDCE47DD-8AD2-4C98-94FF-7769D0BEE1C2.html
- To view the current TLS versions, you can connect to an ESXi host and run openssl commands similar to the following:
   + openssl s_client -tls1 -connect localhost:443 | head -5
   + openssl s_client -tls1_1 -connect localhost:443 | head -5
   + openssl s_client -tls1_2 -connect localhost:443 | head -5
     
```
cd /usr/lib/vmware-TlsReconfigurator/EsxTlsReconfigurator/
./reconfigureEsx vCenterHost -h host-04.faradis.net -u Administrator@vsphere.local -p TLSv1.2
```

### Disable TLS Version ESXi Hosts
https://superuser.com/questions/1328395/esxi-tls-configuration
- For port 443 (HTTPS) on ESXi

```
        vi /etc/vmware/rhttpproxy/config.xml
        Then, search the <ssl> section and change the line
                <!-- <protocols>tls1.0,tls1.1,tls1.2</protocols> -->
        to
                <protocols>tls1.1,tls1.2</protocols>
        Then, restart the web UI :
                /etc/init.d/rhttpproxy restart
```
- For port 5989 (CIM) on ESXi:
```
       1-vi /etc/sfcb/sfcb.cfg
       2- enableTLSv1: false
          enableTLSv1_1: false
          enableTLSv1_2: true

       3- Restart the CIM service by running this command:
                /etc/init.d/sfcbd-watchdog restart
```
- For port 8182 (FDM) on ESXi:
```
         /etc/opt/vmware/fdm/fdm.cfg
```

- For port 9080 (iofilterVP) on ESXi
```
```

-------------------------------------------------------------------------------------------------------------------
### Disable weak ciphers on Esxi:
https://knowledge.broadcom.com/external/article/320798/disabling-static-ciphers-for-tls-in-esxi.html
