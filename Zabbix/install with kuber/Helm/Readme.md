### install with Helm
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
- 
```
kubectl get svc -n monitoring
```
### Nodport
- method1
```
kubectl port-forward svc/zabbix-zabbix-web -n monitoring 8080:80
```
- method2 : run in background
```
nohup kubectl port-forward svc/zabbix-zabbix-web -n monitoring 8080:80 > port-forward.log 2>&1 &
```
### HAProxy
```

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: zabbix-web-ingress
  namespace: monitoring
spec:
  ingressClassName: haproxy
  rules:
  - host: zabbix.faradis.net
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: zabbix-zabbix-web
            port:
              number: 80

```
### HAProxy Loadbalancer
```
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
  type: LoadBalancer

```

### verify:
```
kubectl get namespaces
```
```
kubectl get pods -n monitoring
```



### Tshoot
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
### auto Scale
```
kubectl autoscale deployment zabbix-zabbix-web -n monitoring --min=2 --max=10 --cpu-percent=50

```
