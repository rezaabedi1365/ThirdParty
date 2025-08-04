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
### Port Forward
```
kubectl get svc -n monitoring
```
- method1
```
kubectl port-forward svc/zabbix-zabbix-web -n monitoring 8080:80
```
- method2
```
nohup kubectl port-forward svc/zabbix-zabbix-web -n monitoring 8080:80 > port-forward.log 2>&1 &
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
