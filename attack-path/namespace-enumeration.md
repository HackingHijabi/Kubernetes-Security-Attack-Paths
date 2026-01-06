## Namespace Enumeration

### Description
Kubernetes namespaces provide logical isolation between workloads and are often used to separate system components from user applications. From an attacker’s perspective, enumerating namespaces is a key step in understanding the scope of access and identifying high-value targets.

Compromise of sensitive namespaces significantly increases the blast radius of an attack.

### Attack Scenario
After authenticating to the Kubernetes API using a compromised service account token, accessible namespaces were enumerated.

The enumeration revealed access beyond the default namespace, including the `kube-system` namespace, which hosts critical Kubernetes control plane components and supporting services.

Access to this namespace confirmed that the compromised service account had elevated permissions and posed a high risk to the overall cluster security.

### Why This Matters
Namespaces are often treated as a security boundary. However, improper RBAC configurations can allow attackers to move freely between namespaces once authenticated.

The `kube-system` namespace is particularly sensitive, as it contains components responsible for cluster operation and management.

### Impact
- Visibility into cluster-wide workloads
- Identification of high-value Kubernetes components
- Increased likelihood of privilege escalation
- Expanded blast radius of compromise

### Evidence
See screenshots demonstrating namespace enumeration and access validation.

### Mapping
- MITRE ATT&CK: Discovery
- Kubernetes Security: Authorization and Namespace Isolation

