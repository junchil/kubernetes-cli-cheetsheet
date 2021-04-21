### pv
```bash
kubectl config use-context k8s
kubectl get pv --sort-by=.metadata.name > /opt/KUCC0010/my_volumes
```

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-analytics
spec:
  capacity:
    storage: 100Mi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteMany
  hostPath:
      path: /pv/data-analytics
```

### pvc