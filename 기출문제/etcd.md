# ETCD Backup and restore
### 들어가기 전에
* 이 문제가 보인다?
  * **snapshot etcdctl 찾는다**
### Backup
```bash
$ ETCDCTL_API=3 etcdctl --endpoints=https://127.0.0.1:2379 \
  --cacert=<trusted-ca-file> --cert=<cert-file> --key=<key-file> \
  snapshot save <backup-file-location>
```
### Restore
```bash
export ETCDCTL_API=3
etcdctl --data-dir <data-dir-location> snapshot restore snapshot.db
```
### etcd.yaml 수정
```yaml
volumes:
- hostPath:
    path: /var/lib/etcd-from-backup
    type: DirectoryOrCreate
  name: etcd-data
```