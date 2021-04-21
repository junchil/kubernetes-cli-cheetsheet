### node

```bash
kubectl describe nodes | grep -i ready | wc -l
kubectl describe nodes | grep -i taints | grep -i noschedule | wc -l
```

```bash
kubectl cordon node1
kubectl drain node1  --ignore-daemonsets --delete-local-data
```

```bash
systemctl start kubelet
systemctl enable kubelet
```