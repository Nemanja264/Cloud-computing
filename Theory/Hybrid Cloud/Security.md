***North-South Network Traffic***  

**North-South traffic,** involves data moving between an internal system and an external network (e.g., internet or external clients).

**ON-PREM SIDE**  

The boundary that divides a network or system from the outside world(end-user apps), including the internet, is called a **security perimeter.**
- ***Perimeter security*** in cloud computing refers to the set of security measures implemented to protect cloud environments from external threats by securing the boundaries of the cloud network.  
It acts as the first line of defense against unauthorized access, cyberattacks, and data breaches.

- **API Gateway secures API endpoints**(key capabilities exposed required by front end to render the app)

**CLOUD SIDE**  

- In K8s worker services communicate to one another
- When end-user accesses the app:
  1. They hit the available end point, where they enter the public cloud (in that layer there is **denial of service protection**)
     
  2. Next, Request is being forward to K8s Worker Node, security policy in there: **Calico/K8s** handles layer 3 security level
     
  3. **ISTIO** used for layer 7 network policies and routing for security
     - **These two can cover network security policies from layer 3 to layer 7**

  5. Request hits services, this is **INGRESS application flow**
      - for external Request services can make, **EGRESS calls**, the same can be configured through ISTIO and Calico
      - ***Egress*** refers to the flow of data moving out of a private network into the public internet or another external network.
      - ***Ingress*** refers to data entering a system or network.

    
<img src="../Images/Screenshot%202025-02-17%20174501.png" height = 350>  



***East-West Network Traffic***  

**East-West traffic** refers to data communication between resources **within the same cloud environment or data center.**
- It involves communication between *virtual machines (VMs), containers, microservices, databases, and storage nodes.*
  - (A web application server communicating with a database server, Microservices in a Kubernetes cluster exchanging data.)

***Cloud (Right Side - Blue & Green Sections)***  

  - Divided into **Customer Managed** (e.g., Kubernetes Workers) and **Cloud Managed** (e.g., Kubernetes Master, VA Registry).
  - The **VA Registry** (probably a container registry) stores application images.
  - The **K8s Master (Kubernetes Master Node)** is responsible for **managing the K8s Worker Nodes.**
  - **Istio & Calico** are used for network security & policy enforcement in Kubernetes.

***Security Features in East-West Traffic***  

  -  **Mutual TLS (mTLS)** is used to encrypt service-to-service communication.*(applied inside the Customer Managed Kubernetes cluster)*
  -  Calico & Istio help enforce network security policies between Kubernetes microservices.
  -  **OpenVPN** ensures secure access to Kubernetes control plane.

- ***Mutual TLS***
    - Mutual Authentication, **mTLS verifies both parties (client & server).**  
    - When a *microservice inside Kubernetes* communicates with another service, both services validate each other’s identity before exchanging data.  
    - **End-to-End Encryption,** even if an attacker gains access to the network, they cannot read the data because it's encrypted.  
    - **Istio (Service Mesh)** automatically manages mTLS for internal Kubernetes traffic.  
    - **Calico (Network Policy Engine)** enforces rules that prevent unauthorized microservices from communicating.  
    - **Examples:** **Prevents Man-in-the-Middle (MITM)** attacks inside Kubernetes (data traffic encrypted), Ensures only trusted microservices can talk to each other, Encrypts sensitive data within the cloud environment  

- ***OpenVPN***  
        - **Secure Connection for Administrators,** Cloud administrators use OpenVPN to connect securely to the K8s Master, only authorized users can configure or             control the cluster.  
        - **Protecting Kubernetes API & etcd Database**  
        - **Preventing External Attacks,** OpenVPN *encrypts admin access* and *hides the Kubernetes API endpoint* from unauthorized users.  
     
- ***etcd database***  
     - Distributed key-value store that serves as **the brain of Kubernetes** by storing all cluster data. **(Stores Cluster Configuration & State, networking             details)**
     - etcd security in Cloud:
       1. **Data Encryption(mTLS)**  
       2. **Role-Based Access Control (RBAC)**, **security mechanism** in Kubernetes that controls **who can do what within a cluster.**
         It ensures that users and services only have the **necessary permissions** to perform their tasks.  
         
           - **Key Components:**  
             1. **Role & ClusterRole** – Define what actions are allowed (read, write, delete) on specific resources.  
             2. **RoleBinding & ClusterRoleBinding** – Assign roles to users, groups, or service accounts.    
       
        3. **Backup & Restore**

           
- ***Control Plane***
  
  **The Kubernetes Control Plane** is the central component that manages and orchestrates the cluster.  
  
  *Key Components of the Control Plane:*  
    - **API Server (kube-apiserver)** – The front-end for Kubernetes that processes API requests and communicates with all other components.
    - **Controller Manager (kube-controller-manager)** – Runs controllers that handle node failures, replication, and endpoint updates.
    - **Scheduler (kube-scheduler)** – Assigns workloads (Pods) to nodes based on resource availability.
    - **etcd** – A distributed key-value database that stores cluster state and configuration.
    - **Cloud Controller Manager (optional)** – Handles cloud-specific integrations (e.g., load balancers, storage provisioning).

- ***DevSecOps***
   - **DevSecOps integrates security into DevOps processes,** ensuring that security is a shared responsibility across the entire software development lifecycle
     (SDLC). It emphasizes **automation, continuous monitoring, and proactive security** from development to deployment.**(before they reach production)**
     
     1. Uses AI/ML for real-time threat detection and automated responses.  
     2. Implements multi-factor authentication (MFA) and least privilege access to secure cloud resources.  
     3. Scans container images for vulnerabilities before deployment.  
     4. Implements security checks at every stage of **the Continuous Integration/Continuous Deployment (CI/CD) process.**  
     5. Enforces security policies automatically to meet regulatory standards (e.g., ISO, SOC2, HIPAA).  
     6. **(IaC Security)** Ensures secure configuration of cloud and containerized environments using tools like **Terraform and Ansible.**  
     7. Uses tools like **SAST (Static Application Security Testing)** and **DAST (Dynamic Application Security Testing)** to identify security flaws in code.
     8. Security is integrated early in the development process, reducing vulnerabilities.  
 
   - ***The VA Registry*** (probably a container registry) stores application images.
    - Ensuring that only trusted, validated, and secure images are used in Kubernetes deployments. After its verified good you can push it in K8s worker  
      - **An Admission Controller,** we can use it to secure that image in K8s.**(used in live deployment (production))**  
        - It acts as a **gatekeeper** that can **validate, mutate, or deny requests** based on predefined rules.
