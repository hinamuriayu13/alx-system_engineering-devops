Description:

This setup constitutes a distributed web infrastructure aiming to alleviate traffic to the main server by distributing some workload to a replica server, managed by a load balancer responsible for balancing the load between the primary and replica servers.

Specifics About This Infrastructure:

    Load Balancer's Distribution Algorithm:
    The HAProxy load balancer employs the Round Robin distribution algorithm, which cycles through each server behind it in turns, considering their weights. This algorithm ensures equitable distribution of processing time among servers. As a dynamic algorithm, Round Robin allows for real-time adjustment of server weights.

    Load-Balancer Enabled Setup:
    The HAProxy load balancer facilitates an Active-Passive setup rather than an Active-Active setup. In an Active-Active setup, workloads are evenly distributed across all nodes to prevent overloading. Conversely, in an Active-Passive setup, not all nodes are actively serving at all times. For instance, if one node is active, the other remains passive or on standby until needed.

    Database Primary-Replica Cluster Operation:
    A Primary-Replica configuration designates one server as the Primary, capable of both read and write operations, while the Replica server handles only read requests. Synchronization of data between the Primary and Replica occurs whenever a write operation is executed on the Primary server.

    Primary vs. Replica Node Roles:
    The Primary node handles all write operations required by the site, while the Replica node primarily processes read operations, thereby reducing read traffic directed to the Primary node.

Issues With This Infrastructure:

    Multiple Single Points of Failure (SPOF):
    The infrastructure suffers from several SPOFs, such as the Primary MySQL database server. If this server goes down, the entire site becomes incapable of making changes. Similarly, the server housing the load balancer and the application server connecting to the primary database server also pose SPOF risks.

    Security Concerns:
    Data transmission lacks encryption via SSL certificates, exposing it to potential interception by hackers. Additionally, the absence of a firewall on any server renders the infrastructure vulnerable to unauthorized access from various IPs.

    Lack of Monitoring:
    Without monitoring systems in place, there is no means of assessing the status of each server, leaving potential issues undetected.
