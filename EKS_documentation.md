#### EKS Architecture
  * With EKS you don't need to manage your master nodes, etcd, and worry about making them highly available; EKS does all those heavy lifting on your behalf.

![EKS-architecture-image](https://github.com/Cloud-Yeti/Cloudyeti-EKS-Series/blob/main/Images/EKS_architecture.jpg)
#### Referral Blogs
  * https://aws.amazon.com/blogs/aws/amazon-elastic-container-service-for-kubernetes/

#### EKS-CTL
  * you can use command line or yaml file to specify the resources for eks-ctl
  * try 
  ```sh
  eksctl create cluster --help
  ```
  * Similarly we are using this for this lab. By default you will be m5.large instances using this utility. And will create it new VPC. So, you can make tweaks as per your need
  ```sh
  eksctl create cluster --version=1.16 --name=eks-cluster  --managed --nodes=2 --alb-ingress-access --region=${AWS_REGION} --node-labels="lifecycle=OnDemand,intent=control-apps" --asg-access
  ```
  ```sh
  Note: you can add flags like (--ssh-public-key <key-pairname>) --vpc-cidr <>, etc) as per your usecase.
  ```
     Another common way of managing cluster that you may see is using the yml config file. 
    
   * https://eksctl.io/usage/creating-and-managing-clusters/
