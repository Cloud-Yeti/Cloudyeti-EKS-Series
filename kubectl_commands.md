#### To get info about all service, and deployments in Kubernetes
```sh
  kubectl get all
```
  
#### To get pods info
```sh
  kubectl get pods -o wide
```
  
#### To get nodes info
```sh
  kubectl get nodes -o wide
```

#### To get inside pod to see the logs
```sh
  kubectl exec -it <podname> -- sh
```

#### To see the logs
```sh
  kubectl logs <podname>
```

#### To see whether the container started or failed on startup, whether the container was able to pull image from ECR
```sh
  kubectl describe pod <podname>
```

#### To delete the pod
```sh
  kubectl delete <deployment> <service>
```
  
#### To create the deployment or service using kubectl
```sh
  kubectl apply -f <filename>
```
 
