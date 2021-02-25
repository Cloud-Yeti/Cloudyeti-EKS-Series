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
  * Similarly we are using this for this lab. By default you will be m5.large instances using this utility. You can similarly create tweaks in terms of naming your own subnets using (--vpc-public-subnets,--vpc-private-subnets flag).
  ```sh
  eksctl create cluster --version=1.18 --name=eks-cluster  --managed --nodes=2 --alb-ingress-access --region=${AWS_REGION} --node-labels="lifecycle=OnDemand,intent=control-apps" --asg-access --ssh-access --node-type t2.micro --tags "project=cloudyeti-eks"
  ```
  ```sh
  Note: you can add flags like (--ssh-public-key <key-pairname>) to ssh into kubernetes nodes (--vpc-cidr <>) to create cluster in existing vpc, etc as per your usecase.
  ```
     Another common way of managing cluster that you may see is using the yml config file. 
    
   * https://eksctl.io/usage/creating-and-managing-clusters/
