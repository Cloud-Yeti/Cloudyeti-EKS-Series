## Managing access to multiple users using configmap

* aws eks --region us-east-1 update-kubeconfig  --name eks-cluster  # this command updates your context as well as ~/.kube/config
* with the above command you will receive the config map rules. You can include append the user to whom you want to give access appending mapUsers in the yaml; see below example
* kubectl edit configmap aws-auth -n kube-system   # Append the mapUsers line below and save it
```yml
# Please edit the object below. Lines beginning with a '#' will be ignored,
# and an empty file will abort the edit. If an error occurs while saving this file will be
# reopened with the relevant failures.
#
apiVersion: v1
data:
  mapRoles: |
    - groups:
      - system:bootstrappers
      - system:nodes
      rolearn: arn:aws:iam::<account_id>:role/<>
      username: system:node:{{EC2PrivateDNSName}}
  mapUsers: |
    - userarn: arn:aws:iam::<account_id>:user/<IAM_USERNAME>
      username: <IAM_USERNAME>
      groups:
        - system:masters
kind: ConfigMap
metadata:
  creationTimestamp: "2020-11-11T00:41:50Z"
  name: aws-auth
  namespace: kube-system
  resourceVersion: "4530"
  selfLink: /api/v1/namespaces/kube-system/configmaps/aws-auth
  uid: 66a3e486-1099-458a-98e0-ca4654ffcd96
```
* Alternatively, you could have above yaml in some yaml file like auth-config.yaml and use something like (kubectl apply -f auth-config.yaml)
* Now you must see config/updated once you save the file
#### After the configMap is updated, On users who require cluster permission side, follow below items:
* The users to get access shold only run one command and every thing works
  * aws eks update-kubeconfig --name eks-cluster-name --region aws-region   # So, that the context updates for other users # see ~/.kube/config and click on docker icon in your docker desktop and hover to kubernetes, you must see new context over there.
