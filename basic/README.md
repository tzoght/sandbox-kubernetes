# Docker
## Building Docker image
docker build -t tzoght/node-http-basic .
## Running Docker image
docker run --detach --name node-http-basic-container -p 8989:8989 tzoght/node-http-basic
## Test it
curl -X  GET http://localhost:8989  
## Login to it
docker container exec -it node-http-basic-container sh
## To stop it
docker container stop node-http-basic-container
## To remove the container
docker container rm node-http-basic-container
## To push it
docker login
docker push tzoght/node-http-basic

# Kubernetes
## Switch context
kubectl config use-context docker-for-desktop
## Is the cluster up ?
kubectl cluster-info
## How many nodes ?
kubectl get nodes
## Deploy a pod 
kubectl run zoght --image=tzoght/node-http-basic --port=8989 --generator=run/v1
## Verify the pods
kubectl get pod 
## To access the pod
kubectl expose rc zoght --type=LoadBalancer --name zoght-http
## To verify the service is up
kubectl get service
## To access the pod
curl -X GET http://localhost:8989
## Scaling up
kubectl get replicationcontrollers

kubectl scale rc zoght --replicas=3




# Kubernetes Dashboard
## Deploy it
kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
## Run the proxy
kubectl proxy
## Access it
### what is the username/password
kubectl config view

Then go to: 

http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
