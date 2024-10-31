Server requirements for on-premise deployment
https://helpx.adobe.com/adobe-connect/adobe-connect-11-tech-specs.html
  Windows:
    Microsoft Windows Server 2016(64-bit), 2019 (64-bit)

https://www.mobinhost.com/mag/install-adobe-connect/
https://www.aparat.com/v/Wjl9X



https://www.aparat.com/v/d61he7n

![image](https://github.com/user-attachments/assets/e8a2c23d-450d-4413-8b25-c166d39d5e1a)


- If you are trying to launch a meeting in Classic mode, you need to have the Adobe Media Servers (AMS) up and recognized by the Connect cluster.
- If you are trying to launch in Standard mode you will need both the Adobe Connect Transmuxing Servers (ACTS) and AMS servers up and recognized by the Connect cluster. 

![image](https://github.com/user-attachments/assets/6447c653-b33f-4146-ad13-e5f0bd4ac524)

Certificate:
https://medium.com/@munteanu210/how-to-install-an-ssl-certificate-on-adobe-connect-589b0d9e0699

C:\Connect\11.0\appserv\conf\server.xml
C:\Connect\Stunnel\conf
c:\Connect\11.0\custom.ini

cert = C:\Connect\stunnel\certs\public_certificate_app-server.pem
key = C:\Connect\stunnel\certs\private_key_app-server.key


