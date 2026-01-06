## Defensive Recommendations

### 1. Enforce Least Privilege for Service Accounts
Service accounts should be granted only the minimum permissions required for their workload.

- Review all RBAC roles and bindings
- Remove wildcard (`*`) permissions
- Avoid cluster-wide roles unless absolutely necessary
- Use namespace-scoped roles by default

This limits the blast radius if a service account token is compromised.


### 2. Disable Automatic Service Account Token Mounting
By default, Kubernetes mounts service account tokens into pods even when they are not required.

- Set `automountServiceAccountToken: false` for workloads that do not need API access
- Explicitly enable token mounting only where necessary

This reduces the likelihood of token exposure through application compromise.



### 3. Restrict Privileged Pod Creation
The ability to create privileged pods should be tightly controlled.

- Prevent non-administrative service accounts from creating privileged pods
- Enforce Pod Security Standards (restricted or baseline)
- Use admission controllers to block unsafe pod configurations

This mitigates the risk of node-level compromise.



### 4. Harden Access to the kube-system Namespace
The `kube-system` namespace contains critical cluster components and should be highly restricted.

- Limit access to trusted administrative roles only
- Monitor access attempts to resources within this namespace
- Regularly audit permissions associated with system namespaces



### 5. Protect and Rotate Kubernetes Secrets
Secrets should be treated as highly sensitive credentials.

- Avoid storing plaintext secrets where possible
- Implement regular secret rotation
- Restrict access to secrets using fine-grained RBAC
- Monitor for unauthorized secret access



### 6. Improve Monitoring and Detection
Early detection significantly reduces impact.

- Enable and review Kubernetes audit logs
- Monitor Kubernetes API usage for anomalous behavior
- Alert on creation of privileged pods or unexpected RBAC changes



### 7. Secure the Application Layer
Initial access originated from application-level misconfigurations.

- Secure CI/CD pipelines and Git hooks
- Apply proper authentication and authorization controls
- Regularly assess externally exposed services for misconfigurations



### Summary
Applying these controls significantly reduces the likelihood of service account abuse, unauthorized namespace access, and node-level compromise in Kubernetes environments.

