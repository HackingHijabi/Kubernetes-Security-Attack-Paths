## Service Account Token Abuse

### Description
Kubernetes service accounts provide pods with credentials to interact with the Kubernetes API. These credentials are issued as bearer tokens and are automatically mounted into pods by default.

If a service account is granted excessive permissions, possession of its token allows an attacker to interact with the Kubernetes API with the same level of access.

### Attack Scenario
Following successful initial access that resulted in remote code execution within a pod, a service account token was identified in the running container. The token was extracted and used to authenticate directly against the Kubernetes API using `kubectl`.

Successful authentication allowed enumeration of accessible namespaces and Kubernetes resources, confirming that the service account permissions exceeded the principle of least privilege.

### Why This Matters
Service account tokens are not tied to a specific pod or IP address. Anyone in possession of the token can authenticate to the cluster until the token is revoked or rotated.

In real-world environments, leaked service account tokens are a common path to cluster-wide compromise.

### Impact
- Unauthorized access to the Kubernetes API
- Enumeration of cluster resources
- Potential privilege escalation depending on RBAC configuration
- Increased blast radius following application compromise

### Evidence
See screenshots demonstrating token discovery and authenticated Kubernetes API access.

### Mapping
- MITRE ATT&CK: Credential Access, Discovery
- Kubernetes Security: Authentication and RBAC

