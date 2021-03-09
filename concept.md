#### What is Kubernetes
  * It is open source container management platform
  * helps you run containers at scale
  * Provides Objects and APIs for building modern application

#### Nodes
  * The machine that make up a Kubernetes cluster are called nodes.
  * There are 2 types of nodes:
    * Master node:
      * Makes up the “Control Plane”
      * Acts as the “brains” of the cluster
    * Worker node:
      * Makes up the “Data Plane”
      * Runs the actual container images (via pods).

#### Kubernetes Objects
  * Kubernetes objects are entities that are used to represent the state of the cluster.
  * An object is a “record of intent” —> once created, the cluster does its best to ensure it exists as defined. This is known as the cluster’s “desired state”
  * Kubernetes is always working to make an object’s “current state” equal to the object’s “desired state”. A desired state can describe:
    * What pods (containers) are running, and on which nodes
    * IP endpoints that map to a logical group of containers
    * How many replicas of a container are running, etc
    * K8S Objects Details:
      * Pod
         * A thin Wrapper around one or more container
      * DaemonSet
         * Implements a single instance of a pod on each worker node
      * Deployment
        * Details how to roll out (or roll back) across versions of your application
      * ReplicaSet
        * Ensures a defined number of pods are always running
      * Job
        * Ensures a pod properly runs to completion
      * Service
        * An abstract way to expose an application running on a set of Pods as a network service.
      * Label
        * Key/Value pair for association and filtering.

#### Control Plane

  * One or more API servers: Entry point for REST / kubectl
  * etcd: Distributed key/value store
  * Controller-manager: Always evaluating current vs desired state
  * Scheduler: Schedules pods to worker nodes


#### Data Plane
  * Made up of worker nodes
  * kubelet: Acts as a conduit between the API server and the node
  * kube-proxy: Manages IP translation and routing

##### Kubectl
  * Once your EKS cluster is ready, you get an API endpoint and you’d use Kubectl, community developed tool to interact with your cluster.
#### Install eksctl
  * https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html

#### Components

```
Components: 


Worker node is the one that does all the heavy lifting for us like: 
It includes container run time eg docker, containerd, etc
Kubelet: 
 * interacts with both container and node
 * starts the pod, inside of which we have the container

Kube proxy: forwards the request

Master node Components: basically does  management task ( control plane) 

ApiServer: acts as a gatekeeper, is an entrypoint to k8s cluster

Scheduler: is intelligent enough to decide where to put the pod on which node.
         : It sees how much resources does the application needs like (CPU’s, RAM’s, etc)

Controller Manager: detects the cluster state changes. (eg. crashing of the pods)

Etcd ( also known as cluster brain ): 
     *  stores the cluster changes and are stored in the key value store
     * is a distributed storage system based on raft algorithm.

```  

#### Besides the master and worker components, the most know componets includes

```
Pod: smallest unit of deployment
Deployments: specification of application lifecycle, includes things like replicas, images, and environment variables
Service: specification for exposing service to outside of the EKS cluster
```

#### Furthermore, we have more interesting concepts to deploy application with different "kind" specification
```
Replicaset: Can be specified as part of deployment manifest file. It includes the copy of pods.
Volumes: Persistent Volumes and Persistent Volumes Claim
  * Preserve data even if the pod crashes. https://kubernetes.io/docs/concepts/storage/persistent-volumes/
  * Persistent Volume Claim (request for storage, which is met by binding the PVC to a persistent volume.)
  * Storage Classes: integrate with cloud providers storage volume system.
Configmaps: store parameters, but are encrypted
Secrets: similar to configmaps, but are base64 encoded
DaemonSet: ensures that all (or some) nodes run a copy of a pod. As nodes are added, pods are added. As nodes are removed, pods are garbage collected
Statefulset: suitable for stateful applications or databases
namespace: helps in creating multiple virtual clusters backed by the same physical cluster.
```
