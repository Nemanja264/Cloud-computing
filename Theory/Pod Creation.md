2 types of Nodes in Kubernetes:  
**1. Control Nodes**  
**2. Compute Nodes**  
- Has 3 components:  
  - **Kubelet** - how the compute node communicates with the control plane(kube-api server), also **managing resources and guaranteeing cluster health**  
  - **CRI(Container Runtime Initiative)** - acts as the main connection between **the kubelet** and **the Container Runtime**(run containers on a host operating system)   
  - **Kube-Proxy**  

***The scheduler*** watches for newly created pods and finds the best node for their assignment(based on resources on), it also checks(asks) if any workloads need to be created  
- **on which Compute Node our newly created Pod should go to**  

***Desired state*** - It is the state that you want your cluster to be in  
- **The Kubernetes API server stores the desired state in etcd**  
- Kubernetes continuously works to ensure the actual state of the system matches the desired state  
- **The Kubernetes Controller Manager** constantly monitors the cluster’s actual state and compares it with the desired state. 
- If there is any difference (drift), Kubernetes takes action to reconcile the difference **(control loop).**  

Steps in Creation(this is happening on Control Node):  
1. Call **Kubectl(Kube Control command),** it calls **kube-api server**(main managment component of kubernetes cluster)  
2. kube-api server does call **authentification**(if its okay make a pod)  
3. kube-api server **writes that Pod create request to etcd**(etcd returns when it makes a successful write  
4. kube-api server returns to me that its created
5. **The Controller Manager** monitors the current state of your cluster through the API Server and makes appropriate changes to keep the application running by ensuring sufficient Pods are in a healthy state.**(to reconcile current and desired state)**  
