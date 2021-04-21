### node

```bash
kubectl get nodes | grep -i ready | wc -l
kubectl describe nodes | grep -i taints | grep -i noschedule | wc -l
```


https://kubernetes.io/docs/tasks/administer-cluster/safely-drain-node/
```bash
kubectl cordon node1
kubectl drain node1  --ignore-daemonsets --delete-local-data
```


```bash
kubectl get node

ssh wk8s-node-0

sudo -i

systemctl status kubelet

systemctl start kubelet

systemctl enable kubelet
```