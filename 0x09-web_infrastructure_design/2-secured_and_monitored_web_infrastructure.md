Description:

This infrastructure comprises three servers dedicated to hosting a web environment that prioritizes security, monitoring, and encrypted traffic transmission.

Specifics About This Infrastructure:

    Firewalls' Purpose:
    Firewalls serve to safeguard the network, particularly the web servers, against unauthorized access by acting as intermediaries between the internal and external networks. They achieve this by screening incoming traffic and blocking any that matches predefined criteria.

    SSL Certificate's Purpose:
    The SSL certificate encrypts traffic flowing between the web servers and the external network, mitigating risks such as man-in-the-middle attacks and network sniffing. By ensuring privacy, integrity, and identification, SSL certificates fortify data transmission security.

    Monitoring Clients' Purpose:
    Monitoring clients are deployed to oversee the servers and the external network. They assess server performance and operations, gauge overall health, and promptly alert administrators to deviations from expected performance. These tools analyze server operations, furnishing administrators with vital metrics while conducting automatic tests to verify server accessibility, measure response times, and flag errors such as corrupt or missing files, security breaches, and other anomalies.

Issues With This Infrastructure:

    SSL Termination at Load Balancer Level:
    Terminating SSL at the load balancer would leave traffic between the load balancer and the web servers vulnerable, as it would remain unencrypted.

    Single MySQL Server Scalability:
    Relying on a single MySQL server poses scalability challenges and increases the risk of a single point of failure for the entire web infrastructure.

    Uniform Server Components Impact:
    The presence of servers with identical components can lead to resource contention, including CPU, memory, and I/O, potentially resulting in suboptimal performance. Additionally, such uniformity complicates issue diagnosis and scalability efforts, hampering overall system flexibility.
