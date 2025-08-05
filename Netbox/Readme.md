
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
```
services:
  netbox:
    ports:
      - "8000:8080"
```

```
cp env.example .env
```

```
docker compose pull
docker compose up -d
```

- Username: admin
- Password: admin 

### Admin Reset Password
```
docker exec -it netbox-docker-netbox-1 bash
python3 /opt/netbox/netbox/manage.py shell
```
```
from django.contrib.auth.models import User
user = User.objects.get(username='admin')
user.set_password('newpassword123')
user.save()
exit()
```

