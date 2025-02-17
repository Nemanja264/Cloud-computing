***North-South Network Traffic***  

**ON-PREM SIDE**  

The boundary that divides a network or system from the outside world(end-user apps), including the internet, is called a **security perimeter.**
- ***Perimeter security*** in cloud computing refers to the set of security measures implemented to protect cloud environments from external threats by securing the boundaries of the cloud network.  
It acts as the first line of defense against unauthorized access, cyberattacks, and data breaches.

- **API Gateway secures API endpoints**(key capabilities exposed required by front end to render the app)

**CLOUD SIDE**  

- In K8s worker services communicate to one another
- When end-user accesses the app:
  1. They hit the available end point, wherethey enter the public cloud (in that layer there is **denial of service protection**)
  2. Next, Request is being forward to K8s Worker Node, security policy in there: **Calico/K8s** handles layer 3 security level
  3. **ISTIO** used for layer 7 network policies and routing for security
  - **These two can cover network security policies from layer 3 to layer 7**
  4. Request hits services, this is **INGRESS application flow**
    - for external Request services can make, **EGRESS calls**, the same can be configured through ISTIO and Calico

    
<img src="../Images/Screenshot%202025-02-17%20174501.png" height = 350>


***East-West Network Traffic***  
