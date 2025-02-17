***Deconstruct***  

**1. identify**

**2. refactor** - Application Refactoring is the rewriting of one or more components of an application, typically to take advantage of public cloud services.   
- ***Glue code*** connects two or more software systems in different environments or otherwise bridges incompatible processes.
  It typically runs as a scheduled job on a server or, in today's cloud-based systems, as a serverless function or Docker container.

**3. deploy**

When user hits the app its important that new API flow, the one that is directly accessing public cloud, continues to work.(10% traffic to Public Cloud, 90% to on-prem)  
Eventually you catch all the errors and **make sure public cloud is error free** then => **you deprecate the old UI(on-prem one) and take advantage of UI on public cloud**

  
<img src="../Images/Screenshot%202025-02-17%20155109.png" height = 350>
