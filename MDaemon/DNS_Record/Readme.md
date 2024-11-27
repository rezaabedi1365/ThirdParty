https://www.netafraz.com/blog/how-to-set-up-spf-dkim-dmarc/

sfp
```
v=spf1 mx ip4:5.160.24.71 -all
```
```
v=spf1 a mx -all
```
verify:
```
nslookup -type=txt faratest.net
```
