## Lab Environment Context

### Environment Type
The security assessment was conducted in a controlled Kubernetes lab environment designed to simulate a small, production-like cluster.

The environment included:
- Containerized applications exposed via HTTP services
- A self-hosted Git service running within the cluster
- Kubernetes namespaces separating system and application workloads

### Access Assumptions
The attacker is assumed to have no prior authenticated access at the start of the assessment.

Initial access was achieved through application-layer weaknesses, which resulted in code execution within a containerized workload. From this foothold, Kubernetes-specific attack paths were explored.

### In-Scope Components
- Application services exposed over HTTP
- Kubernetes API access via compromised service account credentials
- Namespace-level and cluster-level resources accessible to the compromised account

### Out-of-Scope Components
- Kubernetes control plane exploitation
- Underlying cloud provider infrastructure
- Physical host security

### Limitations
This assessment reflects the security posture of the lab environment at the time of testing. Findings and impact may vary depending on Kubernetes version, configuration, and deployed security controls.

### Purpose
This environment was used solely for educational purposes to demonstrate common Kubernetes attack paths and associated risks.

