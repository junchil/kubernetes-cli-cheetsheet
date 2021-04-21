### pod

**Creat a pod**
```bash
kubectl run nginx --image=nginx
```

```bash
kubectl run redis --image=redis123 --dry-run=client -o yaml > redis.yaml
```

```bash
kubectl describe pod newpods | grep -w Image
```

```bash
kubectl config use-context k8s
kubectl logs foobar | grep file-not-found > /opt/KULM00201/foobar
```

```bash
kubectl config use-context k8s
kubectl top pods -l name=cpu-utilizer
```

https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    env: test
spec:
  containers:
  - name: nginx
    image: nginx
    imagePullPolicy: IfNotPresent
  nodeSelector:
    disktype: ssd
```

https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-initialization/#creating-a-pod-that-has-an-init-container
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: init-demo
spec:
  containers:
  - name: nginx
    image: nginx
    command: ['sleep', '76800']
    ports:
    - containerPort: 80
    volumeMounts:
    - name: workdir
      mountPath: /workdir
    livenessProbe:
	  exec:
	    command:
		- cat
		- /workdir/calm.txt
  # These containers are run during pod initialization
  initContainers:
  - name: install
    image: busybox
    command: ['sh', '-c', 'mkdir -p /workdir && touch /workdir/calm.txt']
    volumeMounts:
    - name: workdir
      mountPath: "/work-dir"
  volumes:
  - name: workdir
    emptyDir: {}
```

https://kubernetes.io/docs/concepts/storage/volumes/#emptydir
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: non-persistent-redis
  namespace: pre-prod
spec:
  containers:
  - name: redis
    image: redis
    imagePullPolicy: IfNotPresent
	  volumeMounts:
    - name: cache-control
      mountPath: /data/redis
  volumes:
  - name: cache-control
    emptyDir: {}
```


https://kubernetes.io/docs/tasks/configure-pod-container/static-pod/
```bash
ssh wk8s-node-1

cat <<EOF >/etc/kubelet.d/manifests/static-web.yaml
apiVersion: v1
kind: Pod
metadata:
  name: static-web
  labels:
    role: myrole
spec:
  containers:
    - name: web
      image: nginx
      ports:
        - name: web
          containerPort: 80
          protocol: TCP
EOF

systemctl daemon-reload

systemctl restart kubelet

systemctl enable kubelet
```