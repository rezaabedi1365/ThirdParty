# install with Helm
```
helm search repo zabbix-community
```
```
helm repo add zabbix-community https://zabbix-community.github.io/helm-zabbix/
helm repo update
```

```
helm install zabbix zabbix-community/zabbix --namespace monitoring --create-namespace
kubectl get pods -n monitoring
```
# Port Forward
- Temporarly
  * kubectl port-forward
  * Kftray (Graphicy)
- Permanently
  * Ingress Controller (HAProxy, NGINX)
  * Kubernetes Service (NodePort, LoadBalancer)
  * iptables
  * NGINX Reverse Proxy (میتواند جزو Ingress یا جداگانه باشد)

 
```
kubectl get svc -n monitoring
```
### kubectl port-forward
- method1
```
kubectl port-forward svc/zabbix-zabbix-web -n monitoring 8080:80
```
- method2 : run in background
```
nohup kubectl port-forward svc/zabbix-zabbix-web -n monitoring 8080:80 > port-forward.log 2>&1 &
```
### Ingress Controller (HAProxy, NGINX)
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: zabbix-ingress
  namespace: your-zabbix-namespace
  annotations:
    kubernetes.io/ingress.class: "haproxy"
spec:
  rules:
  - host: zabbix.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: zabbix-service
            port:
              number: 80


```
### Kubernetes Service (NodePort)
```
apiVersion: v1
kind: Service
metadata:
  name: zabbix-service
  namespace: your-zabbix-namespace
spec:
  type: NodePort
  selector:
    app: zabbix
  ports:
  - protocol: TCP
    port: 80          # پورت داخلی سرویس
    targetPort: 80    # پورت داخل پاد Zabbix
    nodePort: 30080   # پورت باز روی نودهای کلاستر برای دسترسی خارجی

```
### Kubernetes Service (loadbalancer)
```
apiVersion: v1
kind: Service
metadata:
  name: zabbix-loadbalancer
  namespace: your-zabbix-namespace
spec:
  type: LoadBalancer
  selector:
    app: zabbix
  ports:
  - protocol: TCP
    port: 80          # پورت سرویس داخلی
    targetPort: 80    # پورت داخل پاد Zabbix

```

# verify:
```
kubectl get namespaces
```
```
kubectl get pods -n monitoring
```



# Tshoot
```
#kubectl describe node <node-name>
kubectl describe pod zabbix-zabbix-web-6f4b768545-j9h28 -n monitoring
```

```
kubectl logs zabbix-postgresql-0 -n monitoring
```

```
kubectl exec -n monitoring -it zabbix-zabbix-web-6f4b768545-j9h28 -- nslookup google.com
```
# auto Scale
```
kubectl autoscale deployment zabbix-zabbix-web -n monitoring --min=2 --max=10 --cpu-percent=50

```
