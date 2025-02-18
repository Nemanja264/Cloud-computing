**A workload** in cloud computing and Kubernetes refers to **any application, process, or service** running in a system.  
It includes containers, virtual machines, functions, or entire applications that consume computing resources.  

***In Kubernetes:*** Pods, Deployments, StatefulSets, DaemonSets.  
**In Cloud:** Virtual machines (VMs), serverless functions (AWS Lambda, Azure Functions).  
**In DevOps:** CI/CD pipelines, batch processing jobs.  

***A Kubernetes Deployment creates Pods → Pods run Containers → Kubernetes allocates them to Nodes based on resource availability***  

***Pods***  
- **Smallest deployable unit** in Kubernetes.  
- It represents a single instance of a running process in the cluster and can **contain one or more containers.**  
- Pods are **temporary**, when a Pod fails, Kubernetes may create a new one (with a different IP).  
- **Use Cases:**  
  - **Running a web server** (e.g., NGINX, Flask) — a single container Pod.  
  - Sidecar pattern — a main app container and a helper container (e.g., a logger or proxy).  
  - **Batch jobs** — for short-lived processes like data processing.  

***Nodes***
- **A Node** is a physical or virtual machine that runs **Pods** in a Kubernetes cluster. ***(serves as a worker in a Kubernetes cluster)***
- provides computing resources **(CPU, memory, storage)** and c**ommunicates with the Kubernetes control plane.**  
- **Master node** manages the cluster and schedules workloads. Runs key components like **API Server, Controller Manager, Scheduler, etcd.**
- **Worker Nodes** run actual applications inside Pods.
    - Communicate with the Master Node.  
    - Have components like **Kubelet, Kube Proxy, Container Runtime (Docker/Containerd).**  
    - *Kubelet* ensures containers are running as defined in Pods.
    - *Kube Proxy* – Manages networking and load balancing.
    -  *Container Runtime* – Runs containers (e.g., Docker, Containerd).  
- Functioning:  
    - The **control plane schedules Pods** on available worker nodes. Kubelet ensures Pods are running and healthy.    
    - If a **Node fails, Kubernetes reschedules** workloads to other Nodes.  

***Container***  
- Lightweight, portable, and isolated **execution environment** that includes the **application code,** libraries, and dependencies  
- Containers inside a Pod communicate using **localhost,** while **Pods talk via Kubernetes networking.**  

**HOW THEY WORK TOGETHER**  
  - **A Node** provides the hardware (compute, network, storage).  
  - **Pods** run on Nodes, grouping one or more Containers.  
  - **Containers** execute the actual application logic inside Pods.  
  - **Kubernetes schedules and manages Pods** across multiple Nodes for scaling, reliability, and automation.  


**StatefulSets**
Workload designed for stateful applications that require:  
- Stable network identities (each pod gets a unique, persistent hostname).  
- Persistent storage (each pod maintains its own volume even after restarts). (Databases like MySQL, PostgreSQL, or MongoDB)  
- Ordered deployment, scaling, and updates (pods are started/stopped in a specific order).  

**DaemonSet**
- A DaemonSet ensures that a specific **Pod runs on every node (or a subset of nodes)** in a Kubernetes cluster.  
- It's typically used for running background services that need to be present on all worker nodes.
