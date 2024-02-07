# Kubernetes

**Authentication**&#x20;

It is recommended to use an IdP server as a provider for user authentication to the Kubernetes API (for example, using OIDC). Cluster admini...&#x20;

It is recommended to use a centralized certificate management service to manage certificates within the cluster (for user and service purposes).&#x20;

User accounts should be personalized.&#x20;

The names of the service accounts should reflect the purpose access rights of the accounts.&#x20;



**Authorization**&#x20;

For each cluster, a role-based access model should be developed.&#x20;

Role-Based Access Control (RBAC) should be configured for the Kubernetes cluster. Rights need to be assigned within the project namespace ba...

All services should have a unique service account with configured RBAC rights.&#x20;

Developers should not have access to a production environment without the approval of the security team.&#x20;

It is forbidden to use user impersonation (the ability to perform actions under other accounts).&#x20;

It is forbidden to use anonymous authentication, except for /healthz, /readyz, /livez.&#x20;

Exceptions should be agreed upon with the security team.

Cluster administrators and maintainers should interact with the cluster API and infrastructure services through privileged access managemen...&#x20;

All information systems should be divided into separate namespaces.&#x20;

It is recommended to avoid the situation when the same maintainer team i...&#x20;

RBAC Rights should be audited regularly (KubiScan, Krane)

Secure work with secrets

Secrets should be stored in third-party storage (HashiCorp Vault, Conjur), or in etcd in encrypted form.&#x20;

Secrets should be added to the container using the volumeMount mechanism or the secretKeyRef mechanism.&#x20;

For hiding secrets in source codes, ...&#x20;



**Cluster Configuration Security**&#x20;

Use TLS encryption between all cluster components.&#x20;

Use Policy engine (OPA, Kyverno).&#x20;

The cluster configuration is recommended to comply with CIS Benchmark except for PSP requirements.&#x20;

It is recommended to use only the latest versions of cluster components (CVE list).

For services with increased security requirements, it is recommended to use a low-level run-time with a high degree of isolation (gVisior, K... Cluster Configuration should be audited regularly (Kube-bench, Kube-hunter, Kubestriker)&#x20;



**Audit and Logging**&#x20;

Log all cases of changing access rights in the cluster.&#x20;

Log all operations with secrets (including unauthorized access to secrets).&#x20;

Log all actions related to the deployment of applications and changes in their configuration.&#x20;

Log all cases of changing parameters, system settings, or configuration of the entire cluster (including OS level).&#x20;

All registered security events (at the cluster level and application level both) should be sent to the centralized audit logging system (SIEM).&#x20;

The audit logging system should be located outside the Kubernetes cluster.&#x20;

Build observability and visibility processes in order to understand what is happening in infrastructure and services (WaveScope)&#x20;

Use third-party security monitoring tool on all cluster nodes (Falco, Sysdig, Aqua Enterpise, NeuVector, Prisma Cloud Compute).&#x20;



**Secure OS configuration**&#x20;

Host administrators and maintainers should interact with cluster nodes through privileged access management systems (or bastion hosts).&#x20;

It is recommended to configure the OS and software following the baseline and standards (CIS, NIST).&#x20;

It is recommended to regularly scan packages and configuration for vulnerabilities(OpenSCAP profiles, Lynis).&#x20;

It is recommended to regularly update the OS kernel version (CVEhound).&#x20;



**Network Security**&#x20;

All namespaces should have NetworkPolicy.&#x20;

Interactions between namespaces should be limited to NetworkPolicy following least privileges prin...&#x20;

It is recommended to use authentication and authorization between all application microservices (Istio, Linkerd, Consul).&#x20;

The interfaces of the cluster components and infrastructure tools should not be published on the Internet.&#x20;

Infrastructure services, control plane, and data storage should be located in a separate VLAN on isolated nodes.&#x20;

External user traffic passing into the cluster should be inspected using WAF.&#x20;

It is recommended to separate the cluster nodes interacting with the Internet (DMZ) from the cluster nodes interacting with internal service...&#x20;



**Secure configuration of workloads**&#x20;

Do not run pods under the root account - UID 0.&#x20;

Set runAsUser parameter for all applications.&#x20;

Set allowPrivilegeEscalation - false.&#x20;

Do not run the privileged pod (privileged: true).&#x20;

It is recommended to set readonlyRootFilesystem - true.&#x20;

Do not use hostPID and hostIPC.&#x20;

Do not use hostNetwork.&#x20;

Do not use unsafe system calls (sysctl): kernel.shm \*, kernel.msg \*, kernel.sem, fs.mqueue. \*&#x20;

Do not use hostPath. Use CPU / RAM limits.&#x20;

The values should be the minimum for the containerized application to work.&#x20;

Capabilities should be set according to the principle of least privileges (drop 'ALL', after which all the necessary capacities for the app...&#x20;

Do not use the default namespace (default).&#x20;

The application should have a seccomp, apparmor or selinux profile according to the principles of least privileges (Udica, Oci-seccomp-bpf-h...&#x20;

Workload configuration should be audited regularly (Kics, Kubeaudit, Kubescape, Conftest, Kubesec, Checkov)&#x20;



**Secure image development**&#x20;

Do not use RUN construct with sudo.&#x20;

COPY is required instead of ADD instruction.

Do not use automatic package update via apt-get upgrade, yum update, apt-get dist-upgrade.&#x20;

It is necessary to explicitly indicate the versions of the installed packages.&#x20;

The SBOM building tools (Syft) can be used to determine the l...&#x20;

Do not store sensitive information (passwords, tokens, certificates) in the Dockerfile.&#x20;

The composition of the packages in the container image should be minimal enough to work.&#x20;

The port range forwarded into the container should be minimal enough to work.&#x20;

It is not recommended to install wget, curl, netcat inside the production application image and container.&#x20;

It is recommended to use dockerignore to prevent putting sensitive information inside the image.&#x20;

It is recommended to use a minimum number of layers using a multi-stage build.&#x20;

It is recommended to use WORKDIR as an absolute path.&#x20;

It is not recommended to use cd instead of WORKDIR.&#x20;

It is recommended to beware of recursive copying using COPY . ..&#x20;

It is recommended not to use the latest tag.&#x20;

When downloading packages from the Internet during the build process, it is recommended to check the integrity of these packages.&#x20;

Do not run remote control tools in a container.&#x20;

Based on the results of scanning Docker images, an image signature should be generated, which will be verified before deployment (Notary, Cosign).&#x20;

Dockerfile should be checked during development by automated scanners (Kics, Hadolint, Conftest).&#x20;

All images should be checked in the application lifecycle by automated scanners (Trivy, Clair, Grype).
