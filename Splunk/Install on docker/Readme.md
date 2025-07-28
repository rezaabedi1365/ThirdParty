
###
```
docker pull splunk/splunk
```

### 
```
docker run -d \
  -p 8000:8000 \
  -p 8088:8088 \
  -p 9997:9997 \
  -e SPLUNK_START_ARGS="--accept-license" \
  -e SPLUNK_PASSWORD="Chang3dP@ss!" \
  --name splunk \
  splunk/splunk:latest
```
-v /your/local/path:/opt/splunk/var

```
docker run -d \
  -p 8000:8000 \
  -p 8088:8088 \
  -p 9997:9997 \
  -e SPLUNK_START_ARGS="--accept-license" \
  -e SPLUNK_PASSWORD="Chang3dP@ss!" \
  -v splunk_data:/opt/splunk/var \
  --name splunk \
  splunk/splunk:latest
```


### docker compose
```
version: '3.8'

services:
  splunk:
    image: splunk/splunk:latest
    container_name: splunk
    ports:
      - "8000:8000"   # Web UI
      - "8088:8088"   # HEC (HTTP Event Collector)
      - "9997:9997"   # Universal Forwarder
    environment:
      - SPLUNK_START_ARGS=--accept-license
      - SPLUNK_PASSWORD=Chang3dP@ss!
    volumes:
      - splunk_data:/opt/splunk/var
    restart: unless-stopped

volumes:
  splunk_data:

```
