
![image](https://github.com/user-attachments/assets/ee8fedcc-1cf0-4817-88ca-47242da37915)
### Install on Ubuntu



### install on docker
```
sudo apt update
sudo apt install -y docker.io docker-compose git
sudo systemctl enable docker
sudo systemctl start docker
```

```
git clone https://github.com/netbox-community/netbox-docker.git
cd netbox-docker
```
- create file docker-compose.override.yml
```
services:
  netbox:
    ports:
      - "8000:8080"
```
- for auto start after host restart
```
services:
  netbox:
    restart: unless-stopped
  postgres:
    restart: unless-stopped
  redis:
    restart: unless-stopped
  redis-cache:
    restart: unless-stopped

```

```
docker compose pull
docker compose up -d
```

- Username: admin
- Password: admin 

### Admin Reset Password
```
docker exec -it netbox-docker-netbox-1 python3 /opt/netbox/netbox/manage.py changepassword admin
```
- show user list
```
docker exec -it netbox-docker-netbox-1 bash python3 /opt/netbox/netbox/manage.py shell
```
```
from users.models import User
User.objects.all()
```
### Create New User
```
docker exec -it netbox-docker-netbox-1 python3 /opt/netbox/netbox/manage.py createsuperuser
```

