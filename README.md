# Basic Kubernetes Operations

## Basic JavaScript server app

```BASH
# check the app
node main.js
# create container image
docker build . -t docker.io/ykv001/myapp:v1 
docker push  docker.io/ykv001/myapp:v1
# Deploy app on K8
kubectl apply -f deployment.yml
kubectl get pods
# Check the deployed app running on K8
kubectl port-forward deployment.apps/myapp 3000:3000 
# CTRL + C
```

### ConfigMaps

```BASH
kubectl create configmap myapp-config \
--from-literal=server-url=http://example.com \
--from-literal=timeout=5000
kubectl get configmap myapp-config
kubectl get configmaps
```

### DaemonSets

```BASH
kubectl apply -f daemonset.yaml
kubectl get daemonsets
```

### Services

```BASH
kubectl apply -f service.yaml
kubectl get services
```

### Secrets

```BASH
kubectl create secret generic myapp-secret \
--from-literal=username=myuser \
--from-literal=password=mysecretpassword
kubectl get secret myapp-secret
```

### Persistent Volume & Persistent Volume Claims

```BASH
kubectl apply -f volume-and-pvc.yaml 
kubectl get pvc
```