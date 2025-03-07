**1) Public Cloud**  
Users get access to servers, storage, network, security, and applications as services delivered by cloud service providers over the internet. 
Using web consoles and APIs, users can provision the resources and services they need.  

**The cloud provider owns, manages, provisions, and maintains the infrastructure, renting it out to customers** either for a subscription charge or usage-based fee.  
**Users don’t own the servers their applications run on or storage their data consumes, or manage the operations of the servers, or even determine how the platforms are maintained.**

User does not have any control over the computing environment and is subject to the performance and security of the cloud provider’s infrastructure.
**providers: (Amazon Web Services, Microsoft Azure, IBM Cloud, Google Cloud Platform, and Alibaba Cloud)**

***Characteristics:*** 
On-demand resources
The sheer number of server and network resources available on the public cloud means that a public cloud is highly available  
if one physical component fails, the service still runs unaffected on the remaining available components.

<img src="Images/Screenshot%202025-02-16%20162955.png" height = 300>  

***Use cases:***  
<img src="Images/Screenshot%202025-02-16%20164420.png" height = 350>  

**2) Private Cloud**  

**Cloud infrastructure provisioned for exclusive use by a single organization comprising multiple consumers, such as the business units within the organization.**  
**It may be owned, managed, and operated by the organization, a third party or some combination of them, and it may exist on or off premises.**  

*Implementation:*  
**Internal -** When the platform is provisioned over an organization's internal infrastructure, it runs on-premises and is owned, managed, and operated by the organization  
**External -** When it is provisioned over a cloud providers infrastructure, it is owned, managed, and operated by the service provider.  

A **VPC(Virtual Private Cloud) is a (external) public cloud** offering that lets an organization establish its own private and secure cloud-like computing environment in a logically isolated part of a shared public cloud.  
**VPC,** organizations can leverage the dynamic scalability, high availability, and lower cost of ownership of a public cloud, while having the infrastructure and security tailored to the organization's unique needs.  

A private cloud is a virtualized environment modeled to bring in the benefits of a public cloud platform without the perceived disadvantages of an open-end shared public platform. ( full control over access, security )  

**Use cases:**  
a) for organizations to modernize and unify their in-house and legacy applications. Moving these applications from their dedicated hardware to the cloud also allows them to leverage the power of the compute resources and multiple services available on the cloud.  

b) organizations are integrating data and application services from their existing applications with public cloud services.  
This allows them to leverage their private cloud's compute capability for the larger jobs while pulling data into an application on a private cloud to leverage public cloud services.

c) gives organizations the ability to build applications anywhere and move them anywhere without having to compromise security and compliance in the process

d) provides businesses with on-demand access to computing resources while ensuring full control over security, compliance, and infrastructure management.

This model is often preferred by companies that handle **sensitive data** or operate in **highly regulated industries such as finance, healthcare, and government.**  
Since the infrastructure is managed **within the organization’s own data center** or by a specialized cloud provider, businesses can customize security measures, enforce compliance policies, and optimize performance according to their needs.

**3) Community Cloud**  

**Cloud infrastructure is provisioned for exclusive use by a specific community of consumers from organizations that have shared concerns (e.g., mission, security requirements, policy, and compliance considerations).  
It may be owned, managed, and operated by one or more of the organizations in the community, a third party, or some combination of them, and it may exist on or off premises.**  

Community cloud approach is used by organizations for the following reasons:  
- The community cloud members work under the same set of security controls.
- The approach provides the members the same attributes like citizenship and authorization controls while giving limited physical and/or logical access to resources.
- It also supports data localization and some data sovereignty requirements based on the location of the community cloud’s data centers. 
- The approach defines a perimeter security model encompassing the community cloud. 


**4) Hybrid Cloud**  

Computing environment that **connects** an organization's **on-premise private Cloud** and **third-party public Cloud**, into a single flexible infrastructure for running the organizations applications and workloads.  

Organizations can choose to run **the sensitive, highly regulated, and mission-critical applications or workloads** with reasonably constant performance and capacity requirements **on private Cloud infrastructure**, while deploying the **less sensitive and more dynamic workloads** on the **public Cloud.**  

***Cloud bursting*** is the practice of dynamically scaling public cloud resources to run workloads when on-premises data center resources are at their peak capacity.  

Hybrid Cloud is **interoperable**, which means that the public and private Cloud services can understand each other's APIs, configuration, data formats, and forms of authentication and authorization.  
A Hybrid Cloud is also **portable.** Since you're no longer locked in with a specific vendor, you can *move applications and data* not just between on-premise and Cloud systems, but also *between Cloud service providers.*  

**Two types:**  
***Hybrid mono Cloud*** is a hybrid Cloud with **one Cloud provider**  
***Hybrid multi-Cloud*** is an open standards-based stack that **can be deployed on any public Cloud infrastructure.**  

*The difference* lies in the flexibility that the **hybrid multi-Cloud offers organizations to move workloads and environments from one vendor to another.**  

***Composite multi-Cloud*** variant of hybrid multi-Cloud, distributes single applications across multiple providers, allowing you to move application components across Cloud services and vendors as needed.  

**Use cases:**  
*SaaS integration*  
*Data and AI integration*  
*Enhancing legacy apps*  
*VMware migration*  
*Leveraging public Cloud services*  
