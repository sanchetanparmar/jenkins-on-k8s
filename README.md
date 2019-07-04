# jenkins-on-k8s
Install Jenkins on Kubernetes

### Create a Namespace
`kubectl create ns jenkins`
### Deploy jenkins 
``` kubectl apply -f jenkins-dep.yaml -n jenkins```
# Create jenkins service to access outside 
```kubectl apply -f jenkins-service.yaml -n jenkins```  

Will use  `NodePort` which will expose Jenkins on all kubernetes node IP’s. 

Once Deployment done. you can get pod details and find jenkins admin intial password 

```kubectl get pods --namespace=jenkins``` 

```kubectl exec -it `kubectl get pods --selector=app=jenkins --output=jsonpath={.items..metadata.name}` cat /var/jenkins_home/secrets/initialAdminPassword```

You will find intial password. Get Node Ip and Open Node IP with port `30000` As we mentioned `NodePort=30000`

Ex. - http://hostname:30000
