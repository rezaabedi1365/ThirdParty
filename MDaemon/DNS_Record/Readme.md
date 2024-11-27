https://www.netafraz.com/blog/how-to-set-up-spf-dkim-dmarc/
- A Record
- PTR Record
- MX Record
- 
# SPF
```
"v=spf1 a mx ip4:185.78.22.0/25 include:_auxspf.axspace.com ~all"
```
```
v=spf1 mx ip4:5.160.24.71 -all
```
```
v=spf1 a mx -all
```
verify:
```
nslookup -type=txt example.com
```
# DKIM 
Create Puplickey in your MDaemon . MDaemon send mail with this Publickey in Header and it will be check in dns DKIM Record.
* Security Manager -> Sender Authentication -> DKIM Signing > Create new puplic and private keys
* this file saved as : c:\MDaemon\PEM\MDaemon\dns_readme.txt

```
"v=DKIM1; p=kkhrtghdcghlhsdgkhdfihgdfhgjkhklgbfjgb..."
"Rr/gargtihgihasdrgujghliuagsdfivgbjhsdgvfbhvgsafh..."
```
verify:
```
nslookup
set q=txt
selectorexample._domainkey.example.com
```

# DMARC  Policy
DMARC Record Generator
* https://easydmarc.com/tools/dmarc-record-generator
![image](https://github.com/user-attachments/assets/d1d46195-c494-4da4-9563-9dd7d58f8262)
 
```
v=DMARC1;p=quarantine;pct=100;rua=mailto:dmarc@example.com;ruf=mailto:dmarcfailure@example.com;ri=86400;aspf=r;adkim=r;fo=1

```
verify:
```
nslookup
set q=txt
x._domainkey.example.com
```

#  MXtool
* https://mxtoolbox.com/SuperTool.aspx

![image](https://github.com/user-attachments/assets/d2b55635-ceaa-40d6-ada7-e00ed24db92e)


# Google Search Consol
* https://search.google.com/search-console/about
- 1- crate gmail
- 2- login to gmail in google search consol
- 3- ...
