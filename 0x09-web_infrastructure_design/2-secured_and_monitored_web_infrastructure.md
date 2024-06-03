# Secured and Monitored Web Infras

1. Reasons for Adding New Components:
- Firewalls for each server to protect against attacks and exploits
- SSL certificate to serve www.foobar.com over HTTPS for secure data transmission
- Monitoring clients to collect logs and send them to the Sumo Logic data collector

2. Firewalls:
Firewalls are network security systems that monitor and control incoming and outgoing network traffic based on predetermined security rules. They establish a barrier between a trusted network and an untrusted network, protecting the internal network from external threats.

3. HTTPS:
The traffic is served over HTTPS to ensure secure data transmission. HTTPS uses Transport Layer Security (TLS) to encrypt the data, unlike the plain text transfer of data over HTTP.

4. Monitoring:
Monitoring provides the capability to detect and diagnose any web application performance issues proactively, allowing for timely identification and resolution of problems.

5. Monitoring Data Collection:
The monitoring tool collects logs from the application server, MySQL database, and Nginx web server. Logs are the automatically produced and time-stamped documentation of events relevant to a particular system.

6. Monitoring Web Server QPS:
To monitor the web server's Queries Per Second (QPS), you would monitor it at both the network and application levels. Since one web server handles 1K QPS, monitoring at these levels would provide insights into the server's performance and help identify any issues.

Issues:
A. SSL Termination at the Load Balancer:
Terminating SSL at the load balancer level can be an issue because decryption is resource and CPU-intensive. Placing the decryption burden on the load balancer enables the server to focus on application tasks, but this approach may still have some drawbacks that need to be considered.

B. Single MySQL Server for Writes:
Having only one MySQL server capable of accepting writes is an issue because if that server goes down, no data can be added or updated, and some application features may not function properly. This lack of redundancy and failover can impact the overall application availability.

C. Servers with Identical Components:
Having servers with the same components (database, web server, and application server) can be problematic because a bug in one component on one server will be present in the other servers as well. This can lead to widespread issues and make it more challenging to isolate and resolve the problem.