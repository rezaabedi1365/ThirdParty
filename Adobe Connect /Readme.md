
https://helpx.adobe.com/adobe-connect/adobe-connect-11-tech-specs.html
# Server requirements for on-premise deployment
   * Windows:
         - Microsoft Windows Server 2016(64-bit), 2019 (64-bit)

# install :
- https://www.linkedin.com/pulse/how-implement-adobe-connect-server-secured-ssl-html5-feature-nima/
- https://www.mobinhost.com/mag/install-adobe-connect/
- https://www.aparat.com/v/Wjl9X
- https://www.aparat.com/v/d61he7n

* Note: If you are trying to launch a meeting in Classic mode, you need to have the Adobe Media Servers (AMS) up and recognized by the Connect cluster.
* Note: If you are trying to launch in Standard mode you will need both the Adobe Connect Transmuxing Servers (ACTS) and AMS servers up and recognized by the Connect cluster. 

![image](https://github.com/user-attachments/assets/6447c653-b33f-4146-ad13-e5f0bd4ac524)

Server Setting :
![image](https://github.com/user-attachments/assets/e1120c52-e049-4865-9881-69bdcc849601)


# How to install an SSL certificate on Adobe Connect?
- https://medium.com/@munteanu210/how-to-install-an-ssl-certificate-on-adobe-connect-589b0d9e0699
```
cert = C:\Connect\stunnel\certs\public_certificate_app-server.pem
key = C:\Connect\stunnel\certs\private_key_app-server.key
```

# Adobe Connect LDAP Synchronization configuration for MS Active Directory:
- https://helpx.adobe.com/adobe-connect/kb/breeze-connect-enterprise-server-ldap.html
- https://www.aparat.com/v/e5128p7

Connection Setting :
![image](https://github.com/user-attachments/assets/d4eb3f2d-8279-4c7e-af84-7897a8df235d)

user profile Mapping:
![image](https://github.com/user-attachments/assets/ab71aa20-c121-4c66-a741-08c543bacb35)

Group Profile Mapping :
![image](https://github.com/user-attachments/assets/94833e45-2692-4de1-b996-b2b859a884b9)

Authentication Setting:
![image](https://github.com/user-attachments/assets/fd2a36f2-db2c-49de-8b8b-1024f8463366)

Synchronization Setting :
![image](https://github.com/user-attachments/assets/4d1d9b51-bb8d-4d19-9a32-c138368e442d)

