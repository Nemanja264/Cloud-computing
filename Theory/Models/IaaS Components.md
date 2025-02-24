***1. Network***  
- The **Network** layer connects all the resources together.  
- It includes **Virtual Private Clouds (VPCs), subnets, load balancers, and firewalls.**

***2. Compute Resources***  
  - ***Compute***  
    - **Compute** refers to **virtual machines (VMs)** that run applications.  
    - Cloud providers offer instances with different CPU, memory, and storage capacities.
    - This is the core of IaaS, **where you deploy workloads like websites, databases, or AI models.**
    - **Example Use Cases:** Web servers, application hosting, and development environments

  - ***GPU***  
    - **GPU instances** are designed for tasks requiring high parallel processing power.
    - Ideal for **machine learning, video rendering** and **scientific simulations.**

  - ***HPC (High-Performance Computing)***
    - **HPC clusters** combine multiple virtual machines for complex tasks like simulations and large-scale data analysis.
    - They leverage distributed computing to achieve high processing power.

***3. Storage***  
**a)Object Storage**  
- Used to store unstructured data like images, videos, and backups.  
- Accessible via REST APIs.
  
**b) Block Storage**  
- Provides storage for virtual machines, like an attached hard drive.  
- Suitable for databases and operating systems.
  
**c) File Storage**  
- Provides shared storage for multiple VMs, like a network file system.  
- Ideal for enterprise applications and file sharing.
  
  
<img src="../Images/Screenshot%202025-02-24%20155355.png" height = 350>  
  
  
***Communication between storage and compute resources***  
  
**Network as the Backbone (Pipes)**
- In cloud computing, the **pipes** represent the **network communication channels** between **resources(compute instances)** and **storage**
- This communication happens over **private IPs, VPCs (Virtual Private Clouds), and subnets.**
- Handles **data transfer** securely with **encryption** and **compression.**
- **Imagine you're running an AI model on a GPU instance:**
  - **Data Retrieval:** The GPU instance (compute) sends an API request to **Object Storage (e.g., AWS S3).**
  - **Processing:** The model processes the images.
  - **Result Storage:** The processed results are written back to **Block Storage** for persistence.
  - **Monitoring:** Network traffic between resources is monitored for latency, throughput, and errors.


**Image Classification Model Training (AWS Example)**  

**1. Data Storage (Object Storage):**
- **Store raw images** in Amazon S3 **(Object Storage).**
- Each image is an object with metadata (like file size and type).
- **S3 endpoint:** https://s3.amazonaws.com/my-ml-dataset/training-images/

**2. Compute (GPU Instance):**
- Launch an **AWS EC2 GPU instance for model training.**
- Install frameworks like TensorFlow or PyTorch.
- GPU speeds up parallel processing for large datasets.

**3. Communication (Pipes/Network):**
- The GPU instance connects to the S3 bucket using the **S3 API** over **HTTPS.**
- **Example Python code for data retrieval:**  
  **import** boto3  
  s3 = boto3.client('s3')  
  s3.download_file('my-ml-dataset', 'training-images/cat1.jpg', 'local-cat1.jpg')  

**4. Model Training(Compute):**  
- The GPU processes images locally while reading batches from storage.

**5. Results Storage:**  
- Once the model is trained, the trained model file (model.h5) is uploaded back to the S3 bucket.
- **This transfer also happens through the network (pipe).**
- **Example:** s3.upload_file('model.h5', 'my-ml-dataset', 'trained-models/model.h5')

**6. Monitoring and Logs:**  
- Training logs and metrics are stored in **CloudWatch (monitoring service).**


<img src="../Images/Screenshot%202025-02-24%20164214.png" height = 350>
