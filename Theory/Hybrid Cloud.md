***Connectivity***  

<img src="Images/Screenshot%202025-02-16%20224654.png" height = 350>

**Application** - Trader
**Services** - Portfolios, MQ  
**Get** - function that gets stock price from IEX API  
**MQ** - notify users when there is change in loyalty or portfolio  
**f** - functions from public cloud that uses serverless capabilities that will send messages to users using # integration 

<img src="Images/Screenshot%202025-02-16%231458"

***Connect:***  

**Cloud VPN tunnel** securely extends your peer network to your Virtual Private Cloud (VPC) network through an IPsec VPN connection.  
**Used so that private cloud can access public cloud.**  
All data transmitted through these tunnels isn't decrypted until reaching the organization's data center, ensuring complete security and privacy.  

***Point of Presence (PoP)*** is a physical location that houses data center compute, storage and networking infrastructure where high-speed connections to the internet are established. **Used for connecting privately to public cloud.**  

***Service Mesh:***  
*Control traffic flows and API calls between services while also gaining visibility into your traffic.*  
This makes calls more reliable and your network more robust, even in adverse conditions, while enabling you to catch issues before they become problems.

***Istio*** is an open source service mesh that helps organizations run distributed, microservices-based apps anywhere.  
Enabling us to create policies for ingress gateaway. Tells the gateaway to route the other traffic, it will use vpn to move 50% traffic to Trader v2  

100% - is traffic, 50% will go to Trader v1 and 50% to Trader v2  

