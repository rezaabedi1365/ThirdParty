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
```
kubectl port-forward svc/zabbix-web -n monitoring 8080:8080
```
