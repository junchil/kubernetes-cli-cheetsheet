### etcd

https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/#backing-up-an-etcd-cluster

```bash
ETCDCTL_API=3 etcdctl --endpoints=https://127.0.0.1:2379 \
  --cacert=<trusted-ca-file> --cert=<cert-file> --key=<key-file> \
  snapshot save <backup-file-location>
```

```bash
ETCDCTL_API=3 etcdctl --endpoints=http://127.0.0.1:2379 \
  --ca-file=/opt/KUCM00302/ca.crt \
  --certfile=/opt/KUCM00302/etcd-client.crt \
  --key=/opt/KUCM00302/etcd-client.key snapshot status /data/backup/etcd-snapshot.db  
```