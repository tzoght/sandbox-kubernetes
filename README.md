# Kuberetes Cheat Sheet

## Cluster
### Switch context
```
kubectl config use-context docker-for-desktop
```

### Is the cluster up ?
```
kubectl cluster-info
```

### How many nodes ?
```
kubectl get nodes
```

## Pods
### Listing Pods
```
kubectl get po --show-labels
```
With label selector
```
kubectl get po -L <label selector>
```

Let’s use label selectors on the pods you’ve created so far. To see all pods you created manually (you labeled them with creation_method=manual), do the following: 

```
kubectl get po -l creation_method=manual 
```

To list all pods that include the env label, whatever its value is: 

```
kubectl get po -l env 
```
And those that don’t have the env label: 

```
kubectl get po -l '!env' 
```




## Kuberetes Dashboard
### Deploy it
```
kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
```
### Run the proxy
```
kubectl proxy
```

### Access it
Then go to: 
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/