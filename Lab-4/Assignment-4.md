# Assignment 4

# Describe Architecture of Kubernetes
  Basic Kubernetes architecture exists in two parts: the control plane and the worker nodes. Each node could be either a physical or virtual machine. Every node also runs pods, which are composed of containers. 
  
## Master Node/plane Components:


  - Etcd: a simple, distributed key value storage which is used to store the Kubernetes cluster data (such as number of pods, their state, namespace, etc), API objects and service discovery details based on the Raft consensus algorithm. It is only accessible from the API server for security reasons.The Master node queries etcd to retrieve parameters for the state of the nodes, pods, and containers.

  - API Server: The API Server is the front-end of the control plane and the only component in the control plane that we interact with directly. Internal system components all REST requests to API server for modifications (to pods, services, replication sets/controllers and others, serving as frontend to the cluster.Also, this is the only component that communicates with the etcd cluster, making sure data is stored in etcd and is in agreement with the service details of the deployed pods.

  - Scheduler: Scheduler watches for new requests coming from the API Server and assigns them to healthy nodes. It ranks the quality of the nodes and deploys pods to the best-suited node based on health, labels & namespaces etc based on round robin. If there are no suitable nodes, the pods are put in a pending state until such a node appears.

  - Controller Manager: runs a number of distinct controller processes in the background (for example, replication controller controls number of replicas in a pod, endpoints controller populates endpoint objects like services and pods, and others) to regulate the shared state of the cluster and perform routine tasks. When a change in a service configuration occurs (for example, replacing the image from which the pods are running, or changing parameters in the configuration yaml file), the controller spots the change and starts working towards the new desired state. The controller watches the objects it manages in the cluster as it runs the Kubernetes core control loops. It observes them for their desired state and current state via the API server. If the current and desired states of the managed objects don’t match, the controller takes corrective steps to drive object status toward the desired state. The Kubernetes controller also performs core lifecycle functions.

## Woker Node Components:
  Below are the main components found on a (worker) node:

  - Kubelet: The kubelet runs on every node in the cluster. It is the principal Kubernetes agent. By installing kubelet, the node’s CPU, RAM, and storage become part of the broader cluster. It watches for tasks sent from the API Server, executes the task, and reports back to the Master. It also monitors pods and reports back to the control panel if a pod is not fully functional. Based on that information, the Master can then decide how to allocate tasks and resources to reach the desired state.
  
  - Kube-proxy: The kube-proxy makes sure that each node gets its IP address, implements local iptables and rules to handle routing and traffic load-balancing. It performs request forwarding to the correct pods/containers across the various isolated networks in a cluster.






