# Deploy Postgresql in Kubernetes

Just for testing and PoC

Create configmap

```
kubectl apply -f 1-postgres-configmap.yaml
```


Create Persistent Volume

```
kubectl apply -f 2-postgres-volume.yaml
```

Create Persistent Volume Claim

```
kubectl apply -f 3-postgres-pvc.yaml
```

Check persistent volume

```
kubectl get pv,pvc
```

Run deployment

```
kubectl apply -f 4-postgres-deployment.yaml
```

Create service

```
kubectl apply -f 5-postgres-service.yaml
```

Connect via pod

get pod 

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
