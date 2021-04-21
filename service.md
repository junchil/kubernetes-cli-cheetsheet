### service

```bash
kubectl get svc test -o wide
kubectl top pods -l 'label=value'
```


```bash
kubectl create deployment nginx-dns --image=nginx
kubectl expose deployment nginx-dns --name=nginx-dns --port=80 --type=NodePort
```


```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - image: nginx
    name: nginx
```
```bash
kubectl create svc nodeport nginx --tcp=80:80
```
```bash
apiVersion: v1
kind: Pod
metadata:
  name: busybox
spec:
  containers:
  - image: busybox
    name: busybox
    command: ['sleep', '867000']
```
```bash
kubectl exec -ti busybox -- nslookup nginx
kubectl get pod nginx -o yaml
kubectl exec -ti busybox -- nslookup <Pod ip>
```