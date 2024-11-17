# Install Bigbluebutton on-permiss server :
1- set hostname  
```
hostnamectl set-hostname bbb.faradis.net
```
verify:
- \etc\hostname
- \etc\hosts
   
2- add dns A record for bbb.faradis.net and set local dns in /etc/netplan/00-installer-config.yaml

vrify:
   ```
    nslookup bbb.faradis.net
    dig elearning.fartest.net 
    dig elearning.faratest.net  @10.10.10.1
   ```

3-docker:

    https://docs.docker.com/engine/install/ubuntu/
 

4- copy certificate to letseccryt

* A - Convert pfx to pem cert and pem key 
  ``` 
   openssl pkcs12 -in filename.pfx -nocerts -out privkey.pem
   openssl pkcs12 -in filename.pfx -clcerts -nokeys -out fullchain.pem
  ```
* B - Replace your cert
  ```
      mkdir -p /etc/letsencrypt/live/bbb.faradis.net
      # copy your certificate and key in this path with tihs names:
          /etc/letsencrypt/live/bbb.faradis.net/fullchain.pem
          /etc/letsencrypt/live/bbb.faradis.net/privkey.pem
  ```

5- install 
  ```
  wget -qO- https://raw.githubusercontent.com/bigbluebutton/bbb-install/v2.7.x-release/bbb-install.sh | bash -s -- -v focal-270 -s bbb.faradis.net -e admin@faradis.net -w -x 
  ```

6- you have error 403 connectiopn refus
* A- convert your certificate pfx to PEM
  + PEM file that contains both the certificate and private key, the following command needs to be used:
  ```
  openssl pkcs12 -in filename.pfx -out fullchain.pem -nodes
  ```

* B- Replace your cert fullchain.pem to bellow path in certbundle.pem for haproxy***
  ```
   1- copy fullchain pem to this place /etc/haproxy/fullchain.pem
   2- change config file and replace fullchain.pem 
   bind *:443,:::443 ssl crt /etc/haproxy/fullchain.pem ssl-min-ver TLSv1.2 alpn h2,http/1.1
   *Note: after complete install replaced default cert den you replace it again and restart haproxy service
   ```

* C- Restart Haproxy Service:
   ``` 
    systemctl restart haproxy
   ```


7- install Greenlight & Keycloak
```
wget -qO- https://raw.githubusercontent.com/bigbluebutton/bbb-install/v2.7.x-release/bbb-install.sh | bash -s -- -w -v focal-270 -s bbb.faradis.net -w -g -k
```

8- after complete install  default Haproxy cert Replace to step 6 . you must replace your Cert again and restart haproxy service
```
 1- copy fullchain pem to this place /etc/haproxy/fullchain.pem
 2- change config file and replace fullchain.pem 
 bind *:443,:::443 ssl crt /etc/haproxy/fullchain.pem ssl-min-ver TLSv1.2 alpn h2,http/1.1
 *Note: after complete install replaced default cert den you replace it again and restart haproxy service
```

9- verify:
    - bbb-conf --check
    - sudo bbb-conf --status
    - dpkg -l | grep bbb-
    - bbb-record --list
 ``` 
    docker ps
            CONTAINER ID   IMAGE                            COMMAND                  CREATED          STATUS          PORTS                                NAMES
            9402f7523278   bigbluebutton/greenlight:v3      "bin/start"              39 minutes ago   Up 39 minutes   127.0.0.1:5050->3000/tcp             greenlight-v3
            e2c1b63f1b52   quay.io/keycloak/keycloak:20.0   "/opt/keycloak/bin/k…"   39 minutes ago   Up 39 minutes   8443/tcp, 127.0.0.1:5151->8080/tcp   keycloak
            2ad3e45390dc   redis:6.2-alpine3.17             "docker-entrypoint.s…"   39 minutes ago   Up 39 minutes   6379/tcp                             redis
            9c5249bfc6c5   postgres:14.6-alpine3.17         "docker-entrypoint.s…"   39 minutes ago   Up 39 minutes   5432/tcp                             postgres
```
```
    docker image ls
            REPOSITORY                  TAG               IMAGE ID       CREATED         SIZE
            bigbluebutton/greenlight    v3                6802b602f8a4   7 weeks ago     538MB
            bbb-soffice                 latest            e00a11fe4e9f   12 months ago   1.02GB
            redis                       6.2-alpine3.17    a9a47a706682   19 months ago   27.1MB
            quay.io/keycloak/keycloak   20.0              97ad0f08436f   21 months ago   559MB
            postgres                    14.6-alpine3.17   420ebe472686   22 months ago   242MB
```
```
    docker network ls
            NETWORK ID     NAME                    DRIVER    SCOPEdo
            2770a3a62b47   greenlight-v3_default   bridge    local
```

```
systemctl status haproxy
            Nov 16 11:41:52 bbb haproxy[135047]: Proxy nginx_or_turn started.
            Nov 16 11:41:52 bbb haproxy[135047]: Proxy nginx_or_turn started.
            Nov 16 11:41:52 bbb haproxy[135047]: Proxy turn started.
            Nov 16 11:41:52 bbb haproxy[135047]: Proxy turn started.
            Nov 16 11:41:52 bbb haproxy[135047]: Proxy nginx started.
            Nov 16 11:41:52 bbb haproxy[135047]: Proxy nginx started.
            Nov 16 11:41:52 bbb haproxy[135047]: Proxy nginx-http2 started.
            Nov 16 11:41:52 bbb haproxy[135047]: [NOTICE] 320/114152 (135047) : New worker #1 (135049) fo>
            Nov 16 11:41:52 bbb haproxy[135047]: Proxy nginx-http2 started.
            Nov 16 11:41:52 bbb systemd[1]: Started HAProxy Load Balancer.

```
8- add user 
```
docker exec greenlight-v3 bundle exec rake admin:create
```
- User account was created successfully!
   + Name: Administrator
   + Email: admin@example.com
   + Password: Administrator1!
   + Role: Administrator
 
# used Ports 

```
root@bbb# netstat -ntlup | grep -v tcp6
tcp        0      0 127.0.0.1:81            0.0.0.0:*               LISTEN      393192/nginx: maste
tcp        0      0 127.0.0.1:82            0.0.0.0:*               LISTEN      393192/nginx: maste
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      507930/haproxy
tcp        0      0 127.0.0.1:3022          0.0.0.0:*               LISTEN      513696/node
tcp        0      0 127.0.0.1:3024          0.0.0.0:*               LISTEN      513698/node
tcp        0      0 127.0.0.1:3026          0.0.0.0:*               LISTEN      513697/node
tcp        0      0 127.0.0.1:3014          0.0.0.0:*               LISTEN      513695/node
tcp        0      0 127.0.0.1:3016          0.0.0.0:*               LISTEN      513509/node
tcp        0      0 127.0.0.1:9001          0.0.0.0:*               LISTEN      513265/node
tcp        0      0 127.0.0.1:4000          0.0.0.0:*               LISTEN      513904/node
tcp        0      0 127.0.0.1:4100          0.0.0.0:*               LISTEN      513920/node
tcp        0      0 127.0.0.1:3008          0.0.0.0:*               LISTEN      513509/node
tcp        0      0 127.0.0.1:4001          0.0.0.0:*               LISTEN      513869/node
tcp        0      0 127.0.0.1:3010          0.0.0.0:*               LISTEN      513695/node
tcp        0      0 127.0.0.1:4101          0.0.0.0:*               LISTEN      513903/node
tcp        0      0 127.0.0.1:9002          0.0.0.0:*               LISTEN      513268/node
tcp        0      0 172.20.190.66:3478      0.0.0.0:*               LISTEN      512626/turnserver
tcp        0      0 127.0.0.1:6379          0.0.0.0:*               LISTEN      47338/redis-server
tcp        0      0 172.20.190.66:7443      0.0.0.0:*               LISTEN      513457/freeswitch
tcp        0      0 172.20.190.66:5066      0.0.0.0:*               LISTEN      513457/freeswitch
tcp        0      0 172.20.190.66:5090      0.0.0.0:*               LISTEN      513457/freeswitch
tcp        0      0 172.20.190.66:5060      0.0.0.0:*               LISTEN      513457/freeswitch
tcp        0      0 127.0.0.1:6011          0.0.0.0:*               LISTEN      2548/sshd: root@pts
tcp        0      0 127.0.0.1:5151          0.0.0.0:*               LISTEN      515469/docker-proxy
tcp        0      0 127.0.1.1:27017         0.0.0.0:*               LISTEN      513328/mongod
udp        0      0 172.20.190.66:5060      0.0.0.0:*                           513457/freeswitch
udp        0      0 172.20.190.66:5090      0.0.0.0:*                           513457/freeswitch
udp        0      0 172.20.190.66:3478      0.0.0.0:*                           512626/turnserver
```
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Document:
- https://docs.bigbluebutton.org/administration/install/
- https://docs.bigbluebutton.org/administration/bbb-conf/
  + sudo bbb-conf --restart
  + bbb-conf --setip example.com


