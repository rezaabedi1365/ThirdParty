https://www.netafraz.com/blog/how-to-set-up-spf-dkim-dmarc/

# sfp
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
  
```
v=DKIM1; p=kkhrtghdcghlhsdgkhdfihgdfhgjkhklgbfjgb...
```
verify:
```
nslookup
set q=txt
selector._domainkey.example.com
```

# DMARC  Policy

```

```
verify:
```
nslookup
set q=txt
x._domainkey.example.com
```

#  MXtool
https://mxtoolbox.com/SuperTool.aspx
![image](https://github.com/user-attachments/assets/d2b55635-ceaa-40d6-ada7-e00ed24db92e)


# Google Search Consol
https://search.google.com/search-console/about
1- crate gmail
2- login to gmail in google search consol
3- ...
