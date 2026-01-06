## Risk and Impact Analysis

### Summary
The compromise of a Kubernetes service account with excessive permissions resulted in unauthorized access to sensitive cluster resources. This access enabled both secret exfiltration and the creation of privileged pods, significantly increasing the attack surface and blast radius of the compromise.

### Technical Impact
The identified misconfigurations allowed an attacker to:
- Read Kubernetes secrets across accessible namespaces
- Deploy privileged pods with elevated permissions
- Gain root-level access to the underlying Kubernetes node
- Interact with workloads beyond the initially compromised application

Root access at the node level enables attackers to inspect, manipulate, or disrupt all containers scheduled on that node.

### Business Impact
In a real-world environment, the observed attack path could lead to:
- Exposure of sensitive credentials and configuration data
- Compromise of multiple applications and services
- Data breaches involving customer or operational data
- Service disruption and loss of availability
- Regulatory and compliance violations, depending on data handled

### Likelihood
High.  
Service account misconfigurations and overly permissive RBAC policies are common in Kubernetes environments, particularly where security hardening has not been prioritized.

### Overall Risk Rating
**Critical**

The combination of credential exposure, excessive permissions, and node-level access represents a severe security risk requiring immediate remediation.

