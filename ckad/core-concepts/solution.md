1.

```sh
kubectl run nginx --image=nginx:1.17.10 --namespace=ckad --port=80 --restart=Never
```

2.

```sh
NGINX_IP=$(kubectl get pod nginx -n=ckad -o=go-template='{{.status.podIP}}')
```

3.

```sh
kubectl run busybox --image=busybox --restart=Never --namespace=ckad --command=true -- wget $NGINX_IP
```

4.

```sh
kubectl logs busybox -n=ckad
```

5. You cannot edit the container specification of a running pod.

```sh
$ kubectl delete pod nginx -n=ckad
$ kubectl run pod nginx --image=nginx:1.17.10 --restart=Never --namespace=ckad --port=80 --env=DB_URL=postgresql://mydb:5432 --env=DB_USERNAME=admin --dry-run=client -o=yaml > nginx.yaml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: nginx
  name: nginx
  namespace: ckad
spec:
  containers:
    - env:
        - name: DB_URL
          value: postgresql://mydb:5432
        - name: DB_USERNAME
          value: admin
      image: nginx:1.17.10
      name: nginx
      ports:
        - containerPort: 80
      resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}
```

6.

```sh
kubectl exec -it nginx -n=ckad -- /bin/bash
root@nginx:/# ls -l
```
