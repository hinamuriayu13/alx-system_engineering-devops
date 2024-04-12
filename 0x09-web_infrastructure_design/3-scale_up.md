Description:

This enhanced web infrastructure represents a scaled-up iteration of the previously described setup. Notably, it eliminates all Single Points of Failure (SPOFs) and relocates each major component—web server, application server, and database servers—to distinct GNU/Linux servers. SSL protection is no longer terminated at the load balancer, and each server's network benefits from firewall protection while being actively monitored.

Specifics About This Infrastructure:

    Firewall Deployment Between Servers:
    The inclusion of firewalls between each server serves to fortify individual server security by shielding against unwanted and unauthorized access attempts. This distributed firewall approach enhances overall network security by safeguarding each server individually.

Issues With This Infrastructure:

    Elevated Maintenance Costs:
    While the decentralization of major components onto separate servers enhances system resilience, it also escalates maintenance costs. Procuring additional servers to accommodate this distributed setup, coupled with increased electricity consumption, amplifies operational expenses. Consequently, a portion of the company's budget must be allocated towards server acquisition and ongoing electricity costs to sustain the expanded infrastructure.


