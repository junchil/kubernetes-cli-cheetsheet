### daemonSet

```bash
kubectl run nginx --image=nginx:1.17.1 -o yaml > nginx-daemonset.yaml
```

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  labels:
    run: nginx
  name: nginx
spec:
  selector:
    matchLabels:
      run: nginx
  template:
    metadata:
      labels:
        run: nginx
    spec:
      containers:
      - image: nginx:1.17.1
        name: nginx
        resources: {}
```