### namespace

```bash
kubectl create namespace website-frontend
```
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: jenkins
  namespace: website-frontend
spec:
  containers:
  - name: jenkins
    image: jenkins
    imagePullPolicy: IfNotPresent
```