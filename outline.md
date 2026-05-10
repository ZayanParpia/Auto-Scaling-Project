\# Project Specification: Secure Elastic Compute Architecture



\## 🎯 Executive Summary

The primary objective of this project was the engineering of a production-grade, secure, and auto-scaling AWS environment. By implementing an EC2 Auto Scaling Group (ASG) behind an Application Load Balancer (ALB), the architecture achieves high availability and horizontal elasticity. The project serves as a showcase for integrating cloud-native security best practices with automated infrastructure management.



\---



\## 🛠️ Technical Component Breakdown



\### 🚦 Traffic Orchestration

\*   \*\*Application Load Balancer (ALB):\*\* Functions as the Layer 7 traffic distributor. Configured with advanced health checks to ensure traffic is only routed to healthy targets across multiple Availability Zones.



\### 🔐 Infrastructure Hardening

\*   \*\*Virtual Private Cloud (VPC) \& Segmentation:\*\* Defined a logically isolated network. Application tiers are deployed within \*\*Private Subnets\*\*, removing direct internet routability and significantly reducing the external attack surface.

\*   \*\*Security Groups \& NACLs:\*\* Implemented stateful and stateless firewall rules to enforce strict ingress/egress filtering based on the principle of least-required connectivity.

\*   \*\*AWS Systems Manager (SSM) Session Manager:\*\* Deprecated the use of traditional SSH (Port 22). Remote administration is performed via SSM, providing a secure, auditable, and browser-based shell access without requiring public IPs or Bastion hosts.



\### ⚡ Elastic Compute \& Orchestration

\*   \*\*Auto Scaling Group (ASG):\*\* Configured for horizontal scaling. The group maintains a desired capacity and dynamically adjusts based on resource demand, ensuring the application remains responsive during peak loads.

\*   \*\*CloudWatch Monitoring:\*\* Leveraged high-resolution metrics and alarms to monitor CPU utilization and network throughput, serving as the telemetry source for ASG scaling actions.



\### 🆔 Identity \& Access Management (IAM)

\*   \*\*Granular Privilege Control:\*\* Developed custom IAM roles utilizing the \*\*Principle of Least Privilege (PoLP)\*\*. Policies were manually audited and restricted to the specific API actions required for each service's operational scope, preventing credential misuse and privilege escalation.



\---



\## 🛡️ Security Strategy: Defense-in-Depth

This architecture employs a multi-layered security strategy:

2\.  \*\*Network Layer:\*\* Private subnet isolation and granular SG/NACL rules.

3\.  \*\*Management Layer:\*\* Zero-SSH policy via SSM Session Manager.

4\.  \*\*Identity Layer:\*\* Custom, scoped-down IAM policies for all compute resources.





\## 📈 Key Outcomes \& Architectural Insights

\*   \*\*Resilience vs. Performance:\*\* Demonstrated that Auto Scaling is a core pillar of resilience, ensuring the system can recover from instance failures without downtime.

\*   \*\*Security-First Engineering:\*\* Validated that security is not a post-deployment "add-on" but must be baked into the networking and identity layers from day one.

\*   \*\*Operational Excellence:\*\* Using the CLI highlighted the importance of automation for scalable and consistent cloud operations.



\---



