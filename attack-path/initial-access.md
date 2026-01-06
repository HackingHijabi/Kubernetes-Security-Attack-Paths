## Initial Access

### Description
Initial access describes how an attacker gains their first foothold into an environment. In Kubernetes-backed applications, this often occurs through exposed services, weak credentials, or insecure application configurations that precede any cluster-level compromise.

### Attack Scenario
During reconaissance, multiple HTTP services were identified. One service exposed an encoded PDF file which, once decoded, revealed valid credentials.  

A second service was running a self-hosted Gitea instance with a known user account. The recovered credentials were reused to authenticate successfully, resulting in access to application secrets and sensitive configuration data.

This initial foothold enabled further enumeration and was later chained with Kubernetes-level misconfigurations.

### Impact
- Unauthorized access to application services
- Ex;osure of credentials and secrets
- Enable lateral movement toward Kubernetes resources
- Serves as an entry point for deeper cluster compromise

### Evidence
See screenshots demonstrating credential discovery, authentication, and secret exposure

### Mapping
- MITRE ATT&CK: Initial Access, Credential Access, Discovery
- OWASP Top 10: Security Misconfiguration, Sensitive Data Exposure


