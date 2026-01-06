# Kubernetes Security Attack Paths

## Overview
This project documents a hands-on Kubernetes security assessment demonstrating how common misconfigurations can be chained to achieve deep cluster compromise.

The walkthrough follows a realistic attacker path, starting from application-level access and progressing to Kubernetes API abuse, sensitive data exposure, and node-level compromise. Each attack step is paired with impact analysis and defensive recommendations.

## Scope
The assessment covers:
- Application-layer weaknesses leading to container-level access
- Kubernetes authentication and service account token abuse
- Namespace enumeration and privilege boundary evaluation
- Exposure of Kubernetes secrets
- Creation of privileged pods and node-level access

All activities were performed in a controlled lab environment for educational purposes.

## Key Findings
- Insecure application configurations can provide an initial foothold inside Kubernetes workloads
- Overly permissive service account permissions enable unauthorized Kubernetes API access
- Improper namespace isolation increases the blast radius of compromise
- The ability to deploy privileged pods can result in root access on Kubernetes nodes

## Risk Summary
The identified attack path demonstrates a **critical security risk**.  
If exploited in a production environment, these issues could lead to widespread service compromise, data exposure, and loss of availability.

## Defensive Focus
This project translates offensive findings into actionable defensive controls, including:
- Least privilege RBAC enforcement
- Service account token hardening
- Pod Security Standards and admission control
- Monitoring and detection of high-risk Kubernetes activities

## Project Structure
- attack-path/  `Attacker techniques and exploitation steps`
- impact-analysis/ `Risk and business impact assessment`
- mitigation/ `Defensive recommendations`
- lab-context/ `Environment and assumptions`
- screenshots/ `Redacted supporting evidence`


## Disclaimer
This project is strictly for educational purposes. No testing was performed on production systems.


## Author
**Toibat Bamigboye**  
Cloud Security | Kubernetes Security | Penetration Testing
