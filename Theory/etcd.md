- ***etcd*** is an open source distributed key-value store used to hold and manage the critical information that distributed systems need to keep running.  
- Most notably, it manages the configuration data, state data, and metadata for Kubernetes, the popular container orchestration platform.

1. **fully replicated** - every node in etcd cluster has access to the full data store
2. **consistent** - every **data read** in etcd cluster **will return the most recent data write**
3. **highly available** - no single point of failure in etcd cluster(can tolerate network partitions and hardware failure)
   - leader node goes down, then **followers elect the new leader that will handle replication for cluster**
4. **fast** - performance depends on storage disk speed
5. **secure** - uses Transport layer security with optional SSL client certificate authentication
6. **simple to use** - app can easily write or read from etcd

- **etcd cluster** always **has a leader** and the **other nodes are followers**(key value data store, here key=7)
- **client** can make write or read request to any node not just leader
  - (read)follower node forward that request to leader node, that will respond with cluster current value of key(follower sends that respond to client)

- **Replication:**
1. **client send request** for changing key to 17
2. **leader forwards request to followers**
3. when **followers changes local data store** it return that to the leader
4. when the majority if followers update their current data, **then leader updates its own data store and return successful write to the client**

<img src="Images/Screenshot%202025-02-21%20161050.png" height = 350>

- **Watch function**:
  - etcd stores Kubernetes **configuration data** and **state data**
  - **Watch function compares these two to each other**
  - **if they go out of sync,** etcd acknowledges kube-api about that and **kube-api will reconfigure the cluster**
