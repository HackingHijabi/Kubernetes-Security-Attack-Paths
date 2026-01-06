## Namespace Enumeration

### Description
Kubernetes namespaces provide logical isolation between workloads and are often used to separate system components from user applications. From an attacker’s perspective, enumerating namespaces is a key step in understanding the scope of access and identifying high-value targets.

Compromise of sensitive namespaces significantly increases the blast radius of an attack.

### Attack Scenario
After authenticating to the Kubernetes API using a compromised service account token, accessible namespaces were enumerated.

The enumeration revealed access beyond the default namespace, including the `kube-system` namespace, which hosts critical Kubernetes control plane components and supporting services.

Access to this namespace confirmed that the compromised service account had elevated permissions and posed a high risk to the overall cluster security.

### Expanded Access Validation
Further enumeration confirmed the ability to read Kubernetes secrets across accessible namespaces.

Additionally, the compromised service account permitted the creation of a privileged pod. This pod was deployed successfully, resulting in root-level access on the underlying node.

### Why This Matters
Namespaces are often treated as a security boundary. However, improper RBAC configurations can allow attackers to move freely between namespaces once authenticated.

The `kube-system` namespace is particularly sensitive, as it contains components responsible for cluster operation and management.

### Impact
- Unauthorized access to sensitive Kubernetes secrets
- Ability to deploy privileged pods
- Root-level access to the underlying node
- Potential compromise of all workloads scheduled on the node
- High likelihood of full cluster compromise


### Evidence
See screenshots demonstrating namespace enumeration and access validation.

### Mapping
- MITRE ATT&CK: Discovery
- Kubernetes Security: Authorization and Namespace Isolation

