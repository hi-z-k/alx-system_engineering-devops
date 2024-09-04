# Distributed Web Infras

## Web Infrastructure Design
### Task 1: Definitions and Explanations

1. **Reasons for adding additional elements:**
   The goal of adding more components is to improve the overall reliability, scalability, and performance of the web infrastructure. Specifically:
   - Adding a second web server allows for a load balancer, which can distribute incoming traffic across multiple servers, preventing a single point of failure.
   - The load balancer helps handle increased traffic volumes and ensures better load distribution, improving the user experience.

2. **Load Balancer Distribution Algorithm:**
   The load balancer uses the Round Robin algorithm, which distributes incoming requests sequentially to the available servers in a circular fashion. This works well when the servers have similar specifications and there are not many persistent connections.

3. **Active-Active vs Active-Passive Setup:**
   The load balancer enables an Active-Active setup, where both web server nodes are actively running simultaneously. This provides better performance and scalability than an Active-Passive setup, where one server is active while the other is in standby.

4. **Database Primary-Replica (Master-Slave) Cluster:**
   The database setup uses a Primary-Replica (Master-Slave) configuration. The master server logs all updates, which are then replicated to the slave servers. This enables read scalability and provides redundancy, as the slaves can take over if the master becomes unavailable.

5. **Difference between Primary and Replica Nodes:**
   - The primary node is the main, authoritative source of the application codebase and data.
   - The replica nodes are copies of the primary, providing redundant application instances and increasing read capacity.

**Issues:**
A. **Single Point of Failure (SPOF):** The single load balancer is a SPOF, as its failure would take down the entire system.
B. **Security:** The lack of HTTPS encryption and firewall leaves the system vulnerable to security threats.
C. **Monitoring:** Without monitoring, it's difficult to identify and address issues proactively, impacting performance and user experience.

