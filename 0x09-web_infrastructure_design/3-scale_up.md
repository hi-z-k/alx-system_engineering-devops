# Scaled Up Web Infrans

For every additional element, why are adding it; we have added one server and one
load balancer. Adding the new server has allowed us to separate each component (web
server; Nginx, Application server; code base and Database; MySQL) in there own server
and yet having one extra server with all the components to serve as a backup if any of
the components or server fails. Each server is being monitored and has a firewall. We
have also added an extra load balancer that will assist in handling more traffic across the
whole infrastructure.

Reasons for Adding New Components:
- Added a new web server to enable load balancing and improve scalability
- Implemented a load balancer to distribute incoming traffic across the web servers
- Added a primary-replica (master-slave) database cluster to improve reliability and read scalability
- Added a backup server with all components to serve as a failover in case of any component or server failure
- Implemented monitoring and firewalls for each server to enhance security and proactive issue detection

Load Balancer Distribution Algorithm:
The load balancer uses the Round Robin algorithm to distribute incoming requests across the web servers. This algorithm sends requests to the servers in a circular fashion, one after the other, to ensure even load distribution.

Active-Active vs Active-Passive Setup:
The load balancer enables an Active-Active setup, where both web server nodes are actively serving requests simultaneously. This provides better performance and scalability compared to an Active-Passive setup, where one server is active while the other is in standby mode.

Database Primary-Replica (Master-Slave) Cluster:
The database setup uses a Primary-Replica (Master-Slave) cluster configuration. The master database server logs all updates, which are then replicated to the slave servers. This allows for improved read scalability by distributing read requests across the slave nodes, as well as providing redundancy and failover capabilities.

Backup Server:
The backup server, containing all the components (web server, application server, and database), ensures high availability and failover in case of any issues with the primary servers. This provides an additional layer of redundancy and reliability to the infrastructure.

Monitoring and Firewalls:
Implementing monitoring and firewalls for each server enhances the overall security of the infrastructure and enables proactive issue detection and resolution.