### Create Media

<img width="967" height="637" alt="image" src="https://github.com/user-attachments/assets/79f11b10-dc8a-4da3-969d-b6965f4978f3" />
<img width="685" height="324" alt="image" src="https://github.com/user-attachments/assets/873de6a9-9dde-4909-8298-1c5af718b9fe" />

### Create Triger Action
<img width="1421" height="536" alt="image" src="https://github.com/user-attachments/assets/a0531770-8351-43d8-a6ac-e090bbcf53ee" />
<img width="1329" height="709" alt="image" src="https://github.com/user-attachments/assets/67573a39-b50d-4787-b88b-5ec66ea14631" />


### Select Media For user
<img width="862" height="223" alt="image" src="https://github.com/user-attachments/assets/80c143e7-a8d4-49ea-9f60-02f76ec67cf9" />


### Test email server
- mailx
- sendmail
- msmtp

```
sudo apt install sendmail
```

sudo nano /etc/mail/sendmail.mc
```
define(`SMART_HOST',`mail.faradis.net')dnl
```
<img width="603" height="327" alt="image" src="https://github.com/user-attachments/assets/3021f2fa-9729-413c-b287-3182dd5b47e4" />

```
sudo m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf
sudo systemctl restart sendmail
```
```
echo "This is a test email" | sendmail -s "Test Email" r.abedi@faradis.net
```
```
tail -f /var/log/mail.log
```

### Test media

send email with user and password
```
curl -X POST -H 'Content-Type: application/json' \
     -d '{
           "jsonrpc": "2.0",
           "method": "user.login",
           "params": {
               "user": "Admin",  # نام کاربری خود را وارد کنید
               "password": "zabbix"  # رمز عبور خود را وارد کنید
           },
           "id": 1
         }' \
     http://localhost:10051/zabbix/api_jsonrpc.php

```
send email with token
```
curl -X POST -H 'Content-Type: application/json' \
     -d '{
           "jsonrpc": "2.0",
           "method": "action.get",
           "params": {
               "output": "extend"
           },
           "auth": "<your_auth_token>",  # توکن دسترسی خودتون رو اینجا قرار بدید
           "id": 1
         }' \
     http://localhost:10051/zabbix/api_jsonrpc.php  # آدرس کانتینر Zabbix

```
