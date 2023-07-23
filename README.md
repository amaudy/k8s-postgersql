# Deploy Postgresql in Kubernetes

Just for testing and PoC

You can run all manifest at once by

```
kubectl apply -f .
```

or following each step below.

### 1. Create configmap

```
kubectl apply -f 1-postgres-configmap.yaml
```


### 2. Create Persistent Volume

```
kubectl apply -f 2-postgres-volume.yaml
```

### 3. Create Persistent Volume Claim

```
kubectl apply -f 3-postgres-pvc.yaml
```

Check persistent volume

```
kubectl get pv,pvc
```

### 4. Run deployment

```
kubectl apply -f 4-postgres-deployment.yaml
```

### 5. Create service

```
kubectl apply -f 5-postgres-service.yaml
```

### 6. Connect via pod

Get running pod 

```
kubectl get pod
NAME                        READY   STATUS    RESTARTS   AGE
postgres-655d75f54b-lz4d7   1/1     Running   0          5m35s
```

then

```
kubectl exec -it postgres-655d75f54b-lz4d7 -- psql -h localhost -U appuser --password -p 5432 appdb
```

Connect via psql 

```
psql -h 192.168.39.196 -U appuser --password -p 31398 appdb
```
