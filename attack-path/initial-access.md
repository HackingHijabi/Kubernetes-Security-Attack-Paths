## Initial Access

### Description
Initial access describes how an attacker gains their first foothold into an environment. In Kubernetes-backed applications, this often occurs through exposed services, weak credentials, or insecure application configurations that precede any cluster-level compromise.

### Attack Scenario
During reconaissance, multiple HTTP services were identified. One service exposed an encoded PDF file which, once decoded, revealed valid credentials.  

A second service was running a self-hosted Gitea instance with a known user account. The recovered credentials were reused to authenticate successfully, resulting in access to application secrets and sensitive configuration data.

Further inspection of the Gitea instance revealed insecure Git hook configuration. By abusing these Git hooks, remote code execution was achieved within a containerized application, providing an initial foothold inside the Kubernetes environment.

### Impact
- Unauthorized access to application services
- Ex;osure of credentials and secrets
- Remote code execution within a container
- Establishes a foothold for Kubernetes-level enumeration and escalation 

### Evidence
See screenshots demonstrating credential discovery, authentication, and secret exposure

### Mapping
- MITRE ATT&CK: Initial Access, Credential Access, Execution
- OWASP Top 10: Security Misconfiguration, Sensitive Data Exposure


