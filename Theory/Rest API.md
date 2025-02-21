- ***REST API (Representational State Transfer Application Programming Interface)*** allows communication between cloud services and applications over the internet using standard HTTP methods.

- ***Endpoint*** is a specific **URL** where an API receives requests to access a particular resource or perform an action. Each endpoint represents an interaction point between the client and the server in cloud computing.
  - **format: https://{base-url}/{resource}/{resource-id}/{action}**


1. **Client Sends a Request**
  - **The client (user, app, or service) sends an HTTP request** to the cloud service’s REST API endpoint.
  - Each request targets a specific **resource (e.g., virtual machine, storage object)** identified by a **URI (Uniform Resource Identifier).**
  - The request includes: **Method**(GET, POST, PUT, or DELETE), **Headers**(Metadata like Content-Type and Authorization), **Body**(Optional, Data for POST or PUT)

2. **Authentication and Authorization**
    - The cloud provider verifies the request using one of these methods: **API Key**(Unique identifier for the user), **OAuth Token**, **IAM Roles**(Assigned permissions)
    - If the credentials are valid, the request proceeds, else server returns a **401 Unauthorized status**

3. **Cloud Server Processes the Request**
   - **The API Gateway** receives the request and forwards it to the appropriate **cloud service**
   - **The cloud service** checks the desired action against the user’s permissions.
   - The system interacts with **etcd** (in Kubernetes) or **database backends** to manage resources.
   - **The cloud controller** updates the desired state, such as launching a new virtual machine.

4. **Server Sends a Response**
   - The cloud service sends an **HTTP response** back to the client
   - The response includes: **Status Code, Headers, Body**(JSON or XML with the result of the request)

5. **Cloud Maintains Desired State (Optional)**
   - If the request involves resource creation or updates, the cloud platform maintains the **desired state.**
     - If you request **3 EC2 instances,** the cloud keeps checking and ensures 3 instances run.

6. **Client Acts on the Response**
   - The client processes the response and takes further action:
     - *Displaying data in an app*
     - *Creating new API calls*
     - *Handling errors*
   - **For example, if the API returns the instance ID, the client can use it for monitoring or termination.**

