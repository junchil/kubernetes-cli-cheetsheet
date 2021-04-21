### deployment

```bash
kubectl create deployment kucc4 --image=nginx,redis,memcached,consul --dry-run -o yaml > kucc4.yaml
```

```bash
kubectl scale  deployment nginx-app --replicas=4
```

```bash
kubectl create deployment nginx-app --image=nginx:1.10.2-alpine
kubectl scale deployment nginx-app --replicas=3 --record
kubectl set image deployment nginx-app nginx=nginx:1.13.0-alpine --record
kubectl rollout undo deployment nginx-app --record
kubectl get deploy nginx-app -o yaml > /opt/xxxxx.yaml
```
