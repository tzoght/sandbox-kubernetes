# Deploy and Run node-http-basic

## Building Docker image
```
docker build -t tzoght/node-http-basic 
```

### Running Docker image
```
docker run --detach --name node-http-basic-container -p 8989:8989 tzoght/node-http-basic
```

### Test it
```
curl -X  GET http://localhost:8989  
```

### Login to it
```
docker container exec -it node-http-basic-container sh
```

### To stop it
```
docker container stop node-http-basic-container
```

### To remove the container
```
docker container rm node-http-basic-container
```

### To push it
```
docker login
docker push tzoght/node-http-basic
```

## Deploying in Kubernetes (K8S for Docker)
### Deploy a pod 
```
kubectl create -f node-http-basic.yml
```

### Verify the pods
```
kubectl get pod 
```

## To expose the pod via an LB service
```
kubectl expose pod app --type=LoadBalancer --name app
```
Then
```
kubectl get service && oepn http://localhost:8989
```


## To verify the service is up
kubectl get service
## To access the pod
curl -X GET http://localhost:8989
## Scaling up
kubectl get replicationcontrollers

kubectl scale rc zoght --replicas=3





