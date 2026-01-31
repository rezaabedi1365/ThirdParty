# up stream Server
### 1-Server Consol
#### setting 
```
Update
   Update Interval: Regular interval 6 Hours
   Update Server: AUTOSELECT | UPSTREEAM ADDRESS
   Update Type : 
Advanced Setting
   HTTP PROXY: off
   SMTP SERVER:
   ACRIVE DIRECTORY:
   SYSLOG SERVER:
   REPOSITORY: AUTOSELECT
   LOGGING: Trace , JSON
   DATABASE CLEAN UP
```
#### Policy
HTTP Proxy usage
```
Depricated
```

Eset Bridge :
```
```


Console Policy :
```
Updates
   - updates : Myprofile
   - Profile :
      + updates :
            * Module updates : Choose automatically : on
                Custeom Server : Blank
            * Application updates : Update mode : Auto-update
               Custeom Server : Choose automatically
      + Connection option:
            * Proxy Server: 
            * Windows Share:
      + update morror: access to update files:
            * http server :  
            * connection option :
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic
```



Client and server Policy :
```
Update : Myprofile
   Module updates : Choose automatically : off
   Custeom Server : http://192.168.54.10:2221
   Application updates : Update mode : Auto-update
   Custeom Server : Choose automatically 
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic


Updates
   - updates : Myprofile
   - Profile :
      + updates :
            * Module updates : Choose automatically : off
                Custeom Server : http://192.168.54.10:2221
            * Application updates : Update mode : Auto-update
               Custeom Server : Choose automatically
      + Connection option:
            * Proxy Server:
            * Windows Share:
      + update morror: access to update files:
            * http server :  
            * connection option :
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic
```


# For downstream server
### 1-Server Consol
#### setting 
```
Update
   Update Interval: Regular interval 6 Hours
   Update Server: AUTOSELECT | UPSTREEAM ADDRESS
   Update Type : 
Advanced Setting
   HTTP PROXY: on / host:172.20.190.12 / port:3128
   SMTP SERVER:
   ACRIVE DIRECTORY:
   SYSLOG SERVER:
   REPOSITORY: AUTOSELECT
   LOGGING: Trace , JSON
   DATABASE CLEAN UP
```
#### Policy
HTTP Proxy usage
```
Depricated
```

Eset Bridge :
```
```


Console Policy :
```
Updates
   - updates : Myprofile
   - Profile :
      + updates :
            * Module updates : Choose automatically : on
                Custeom Server : Blank
            * Application updates : Update mode : Auto-update
               Custeom Server : Choose automatically
      + Connection option:
            * Proxy Server:
            * Windows Share:
      + update morror: access to update files:
            * http server :  
            * connection option :
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic
```



Client and server Policy :
```
Update : Myprofile
   Module updates : Choose automatically : off
   Custeom Server : http://12.2.2.2:2221
   Application updates : Update mode : Auto-update
   Custeom Server : Choose automatically 
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic


Updates
   - updates : Myprofile
   - Profile :
      + updates :
            * Module updates : Choose automatically : off
                Custeom Server : http://192.168.54.10:2221
            * Application updates : Update mode : Auto-update
               Custeom Server : Choose automatically
      + Connection option:
            * Proxy Server:
            * Windows Share:
      + update morror: access to update files: Create update mirror: on / storage folder : C:\ESETMirrorUpdate / server port :2221
            * http server : Enable http server : on 
            * connection option :
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic
```









# For isolated network with mirror update
### 1-Server Consol
#### setting 
```
Update
   Update Interval: Regular interval 6 Hours
   Update Server: AUTOSELECT | UPSTREEAM ADDRESS
   Update Type : 
Advanced Setting
   HTTP PROXY: off
   SMTP SERVER:
   ACRIVE DIRECTORY:
   SYSLOG SERVER:
   REPOSITORY: AUTOSELECT
   LOGGING: Trace , JSON
   DATABASE CLEAN UP
```
#### Policy
HTTP Proxy usage
```
Depricated
```

Eset Bridge :
```
```


Console Policy :
```
Updates
   - updates : Myprofile
   - Profile :
      + updates :
            * Module updates : Choose automatically : on
                Custeom Server : Blank
            * Application updates : Update mode : Auto-update
               Custeom Server : Choose automatically
      + Connection option:
            * Proxy Server:
            * Windows Share:
      + update morror: access to update files:
            * http server :  
            * connection option :
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic
```



Client and server Policy :
```
Update : Myprofile
   Module updates : Choose automatically : off
   Custeom Server : http://12.2.2.2:2221
   Application updates : Update mode : Auto-update
   Custeom Server : Choose automatically 
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic


Updates
   - updates : Myprofile
   - Profile :
      + updates :
            * Module updates : Choose automatically : off
                Custeom Server : http://192.168.54.10:2221
            * Application updates : Update mode : Auto-update
               Custeom Server : Choose automatically
      + Connection option:
            * Proxy Server:
            * Windows Share:
      + update morror: access to update files: Create update mirror: on / storage folder : C:\ESETMirrorUpdate / server port :2221
            * http server : Enable http server : on 
            * connection option :
Connectivity:
   Proxy Server :
      Use proxy Server : off
   License:
      Interval check : Automatic
```

