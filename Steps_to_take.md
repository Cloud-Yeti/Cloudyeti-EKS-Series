### Provision a EKS cluster using EKS CTL utility
![1](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/1.png) <br />
### EKSCTL creates a cloudformation stack for spinning up resources
![2](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/2.png) <br />
### You can see the status of EKS cluster in EKS management console
![3](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/3.png) <br />
### If you have different EKS cluster, you can switch back and forth between the EKS cluster using Kubernetes context
```
aws eks --region us-east-1 update-kubeconfig  --name eks-cluster
```
![4](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/4.png) <br />
### Easy way to spin up applications in EKS Cluster
![5](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/5.png) <br />
### NodePort can be used for local development, but it's not recommended for production workloads
``` 
Now open ExternalIpPort:Nodeport on the browser. In the below example -> 3.21.12.58:30301
```
![6](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/6.png) <br />
### To see the application in UI, we need to open 30301 on security group which is NodePort security group that we have specified on service manifest file
![7](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/7.png) <br />
### The better approach is to use loadbalancer in service file. You can see following security groups entries after the service is created with load balancer
![8](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/8.png) <br />
### The network load balancer is being provisioned as we have provided specification on service file
![9](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/9.png) <br />
### You can now browse the application with loadbalancer:applicationPort
![10](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/10.png) <br />
### The eksctl utility creates a autoscaling for our nodes. If you spin down the instance. It will autoprovision.
![11](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/11.png) <br />
### Instances brought back by autoscaling, since we have our specification in launch template created by eksctl utility
![12](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/12.png) <br />
### Now, you can see our application is brought back with the same load balancer endpoint. 
![13](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/13.png) <br />
### [Managing Users and RBAC in EKS](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/managing_users_and_RBAC.md) <br />
### Let's not forget to bring down the cluster to save our bills after workshop
![14](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/14.png) <br />
### You can see, the cloudformation stack get's deleted, which deletes every resources including EKS Cluster, launch template, security groups, IAM, etc.
![15](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/15.png) <br />

## Thanks for following
