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

  -Mutual TLS
    - Mutual Authentication, **mTLS verifies both parties (client & server).** When a *microservice inside Kubernetes* communicates with another service, both services validate each other’s identity before exchanging data.
