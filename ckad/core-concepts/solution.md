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

7.  Status is `Completed`

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: loop
  namespace: ckad
  labels:
    name: loop
spec:
  containers:
    - name: loop
      image: busybox:latest
      args:
        - /bin/sh
        - -c
        - for i in {1..10}; do echo "Welcome $i times"; done
  restartPolicy: Never
```

8.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: loop
  namespace: ckad
  labels:
    name: loop
spec:
  containers:
    - name: loop
      image: busybox:latest
      args:
        - /bin/sh
        - -c
        - while true; do echo "Hello"; done
  restartPolicy: Never
```

9. Status is `Running`

10.

```sh
kubectl delete ns ckad
```

11.

```sh
$ kubectl create ns mynamespace
$ kubectl run nginx --image=nginx -n=mynamespace
```

12.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  namespace: mynamespace
  labels:
    app: nginx
spec:
  containers:
    - name: nginx
      image: nginx:latest
  restartPolicy: Never
```

13.

```sh
kubectl run busybox --image=busybox --command env

```

14.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: busybox
  labels:
    app: busybox
spec:
  containers:
    - name: busybox
      image: busybox:latest
      args:
        - /bin/sh
        - -c
        - env
  restartPolicy: Never
```

15.

```sh
kubectl create ns myns --dry-run=client -o=yaml > myns.yaml
```

```yaml
apiVersion: v1
kind: Namespace
metadata:
  creationTimestamp: null
  name: myns
spec: {}
status: {}
```

16.

```sh
$ k create resourcequota myrq --hard=cpu=1,memory=1G,pods=2 --dry-run=client -o=yaml
```

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  creationTimestamp: null
  name: myrq
spec:
  hard:
    cpu: "1"
    memory: 1G
    pods: "2"
status: {}
```

17.

```sh
$ k get pods --all-namespaces
```
