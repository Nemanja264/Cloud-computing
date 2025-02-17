***Deconstruct***  

- next for steps are used to break out individual portions out of monolithic architecture and move it to a public cloud
  
**1. identify**

**2. refactor**  
- ***Glue code*** connects two or more software systems in different environments or otherwise bridges incompatible processes.
- ***Refactoring (Cloud-Native Migration):*** Redesign applications to be fully optimized for cloud services like serverless computing, Kubernetes, or microservices. Typically to take advantage of public cloud services.   

**3. deploy**

When user hits the app its important that new API flow, the one that is directly accessing public cloud, continues to work.(10% traffic to Public Cloud, 90% to on-prem)  
Eventually you catch all the errors and **make sure public cloud is error free** then => **you deprecate the old UI(on-prem one) and take advantage of UI on public cloud**

  
<img src="../Images/Screenshot%202025-02-17%20155109.png" height = 350>

**4. repeat**  

***Lift and Shift***

- **Lift and shift—moving** the process of migrating an exact copy of an application or workload, together with its data store and operating system (OS), from IT one environment to another—usually from on-premises to public or private cloud.
This is also sometimes referred to as **rehosting.**
- Used when we dont have time to refactor, some older applications may not be designed for the cloud and rewriting them would be expensive and time-consuming.
- *Quick Cloud Migration Requirements,* when an organization needs to move to the cloud rapidly due to data center closure, cost-cutting, or disaster recovery needs

GET - gets us stock prices  
- portfolio calls it and it returns stock price to portfolio
- better way call GET directly from UI of public cloud
  
<img src="../Images/Screenshot%202025-02-17%20161551.png" height = 350> 


Serverless technology
- f - function as a service, hits IEX public APIs (taking advantage of IEX APIs using serverless)
- then repeat all the 4 steps from deconstruct, after that we **test new serverless workflow**
- **after verifying workflow works well** then => **we can cut out monolithic architecture that we pulled in public cloud**
  
<img src="../Images/Screenshot%202025-02-17%20163656.png" height = 350>

