
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
<img width="976" height="502" alt="image" src="https://github.com/user-attachments/assets/53b51503-d095-49ba-b053-58af68ca04d9" />

<img width="979" height="499" alt="image" src="https://github.com/user-attachments/assets/05d0b114-effa-4fb2-85e8-4650c59810f8" />


# How to install an SSL certificate on Adobe Connect?
- https://medium.com/@munteanu210/how-to-install-an-ssl-certificate-on-adobe-connect-589b0d9e0699
```
cert = C:\Connect\stunnel\certs\public_certificate_app-server.pem
key = C:\Connect\stunnel\certs\private_key_app-server.key
```

# Adobe Connect LDAP Synchronization configuration for MS Active Directory:
- https://helpx.adobe.com/adobe-connect/kb/breeze-connect-enterprise-server-ldap.html
- https://www.aparat.com/v/e5128p7

### Connection Setting :
<img width="978" height="632" alt="image" src="https://github.com/user-attachments/assets/cf1edd8b-09c2-4cc9-a502-929448054f73" />


### user profile Mapping:
<img width="973" height="770" alt="image" src="https://github.com/user-attachments/assets/39810c6c-9b44-4ff6-9fd8-25ee0eb023d1" />


### Group Profile Mapping :
<img width="973" height="649" alt="image" src="https://github.com/user-attachments/assets/e65e2d2e-edf8-46ce-8c02-5b3ceeca9937" />


### Authentication Setting:
<img width="977" height="633" alt="image" src="https://github.com/user-attachments/assets/af838885-4e86-4716-9473-198969df604a" />

### Synchronization Setting :
- Schedule Synchronization
<img width="972" height="470" alt="image" src="https://github.com/user-attachments/assets/85a5a2aa-fe4d-4f00-b847-bab53af125e2" />

- Manual Synchronization
<img width="969" height="624" alt="image" src="https://github.com/user-attachments/assets/10c6447c-763a-4d65-8aa3-41947bc31d4c" />


### Right to left Email Format
```
<div style="direction: rtl; text-align: right; font-family: Tahoma, sans-serif; line-height: 1.8;">
همکار محترم<br><br>
کلاسی تحت عنوان "<strong>مدیریت</strong>" برای شما با مشخصات زیر در نظر گرفته شده است.  
در زمان مقرر از طریق لینک ذیل در کلاس حضور به‌عمل آورید.<br><br>
<strong>زمان:</strong> {meeting-time}<br>
<strong>لینک ورود به کلاس:</strong><br>
{meeting-url}<br><br>

مدیریت سرمایه‌های انسانی
</div>

```
