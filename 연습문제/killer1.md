# Q1. context
$ k config get-contexts 
$ k config current-context 

# Q2. scheduled container
* Taint
### just run a pod
$ kubectl run pod1 --image dockerimage:tag 
* toleration 필요함

# Q3. Scale down
$ kubectl -n project-c13 scale sts o3db --replicas 1

# Q4. 
$ kubectl run am-i-ready --imager nignx:1.16.1-alpine --labels "id=cross-server-ready"

# Q5. Get all pods
$ echo 'kubectl get pods --all-namespaces --sort-by=metadata.creationTimestamp

# Q6. 

# Q11. role / rolebinding
$ kubectl create sa processor
$ kubectl create role processor --verb=create --resource configmap --resource secret

# Q12. deployment
$ kubectl create deployment deploy-important --labels "id=very-important" -o 
```
spec:
  topologySpreadConstraints:
  - maxSkew: 1
    topologyKey: zone
    whenUnsatisfiable: DoNotSchedule
    labelSelector:
      matchLabels:
        foo: bar
```

# Q13. sidecar 패턴
* create volume in deployment.template.spec

# Q14. cluster info
* how many controlplane nodes: k get nodes: 1
* how many worker nodes: k get nodes: 2
* what is service cidr ssh controlplane cat /etc/kubernetes/api-server.yaml | grep service > 10.0.0.0/12
* which networking is configured and where
* which suffix: -{name} like cluster-node => -cluster-node1

# Q15. cluster logging
$ k get events
$ k delete pods -n kube-system kube-proxy-abc
$ k logs -n kube-system
