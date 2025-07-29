# Kubernetes

####  Autenticação e Administração do Cluster

* **IdP externo (OIDC)** – integre a API Server a um provedor de identidade (Okta, Keycloak, Azure AD) para autenticar usuários.
* **Gerenciamento de certificados** – centralize a emissão/rotação (cert‑manager, HashiCorp Vault PKI).
* **Contas de usuário** – sempre personalizadas; proíba contas genéricas ou compartilhadas.
* **ServiceAccounts** – nomeie‑as de forma indicativa (`sa-readonly-logs`) e limite‑as ao estritamente necessário.

***

#### 2 · Autorização (RBAC)

* **Modelo de papéis por cluster** – defina funções, grupos e namespaces antes do go‑live.
* **Granularidade por namespace** – atribua permissões dentro do namespace do projeto; nunca diretamente em nível de cluster, salvo justificativa.
* **ServiceAccounts exclusivas** – um serviço ⇢ uma ServiceAccount ⇢ um Role/RoleBinding.
* **Acesso de desenvolvedores a produção** – requer aprovação formal da equipe de segurança.
* **Proibições**
  * **User impersonation** (`--as`)
  * **Autenticação anônima**, exceto para `/healthz`, `/readyz`, `/livez` mediante acordo.
* **PAM/Bastion** – administradores devem acessar API Server e nós via gerenciamento de acesso privilegiado.
* **Auditoria de RBAC** – rode **KubiScan** ou **Krane** periodicamente.

***

#### 3 · Segredos

* **Armazenamento protegido** – HashiCorp Vault, CyberArk Conjur ou etcd _encrypted at rest_.
* **Injeção em pods** – `volumeMount` ou `secretKeyRef`; nunca hard‑code.
* **Ciclo de vida** – rotação automática e remoção de segredos órfãos.

***

#### 4 · Segurança da Configuração do Cluster

* **TLS everywhere** – API Server ⇄ kubelet, etcd, webhook, etc.
* **Políticas admission controllers** – OPA/Gatekeeper ou Kyverno.
* **CIS Kubernetes Benchmark** – aplique todo o baseline (exceto PSP depreciado).
* **Versões recentes** – monitore CVEs e atualize componetes frequentemente.
* **Runtimes de alta isolação** – gVisor, Kata Containers, Firecracker para workloads sensíveis.
* **Auditoria** – **kube‑bench**, **kube‑hunter**, **Kube‑Striker** agendados.

***

#### 5 · Auditoria & Observabilidade

* **Registre**
  * Mudanças de RBAC
  * Acesso/criação de segredos
  * Deploys e alterações de ConfigMaps/Secrets
  * Alteração de parâmetros do cluster ou do SO
* **Centralize logs** em SIEM fora do cluster.
* **Ferramentas** – Falco, Sysdig Secure, Aqua Starboard, NeuVector, Prisma Cloud.
* **Dashboards** – implemente pipelines de telemetria (WaveScope, Grafana/Loki/Tempo).

***

#### 6 · Configuração Segura do Sistema Operacional

* **Acesso via bastion/PAM** – sem SSH direto nos nós.
* **Baseline CIS/NIST** – aplique hardening automático (Ansible, Chef InSpec).
* **Vulnerability scanning** – OpenSCAP, Lynis, CVEHound para kernel.
* **Patch management** – atualize kernel e pacotes críticos regularmente.

***

#### 7 · Segurança de Rede

* **NetworkPolicy obrigatória** – por namespace, princípio do menor privilégio.
* **Service‑to‑Service mTLS** – Istio, Linkerd ou Consul Connect.
* **Plano de controle isolado** – componentes internos em VLAN dedicada, sem exposição direta à Internet.
* **WAF** – inspecione todo tráfego externo que entra no cluster.
* **DMZ lógica** – separe nós que acessam Internet dos nós only‑internal.

#### Configuração Segura de Workloads

```yaml
yamlCopiarEditarsecurityContext:
  runAsUser: 1000          # nunca root (UID 0)
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: true
  capabilities:
    drop: [ "ALL" ]        # adicione apenas as necessárias
```

* **Proibições**: `privileged: true`, `hostPID`, `hostIPC`, `hostNetwork`, `hostPath`.
* **Limites de recursos** – CPU e memória mínimos viáveis.
* **Profiles** – seccomp, AppArmor ou SELinux; gerar com Udica/oci‑seccomp‑bpf.
* **Auditoria** – Kics, kubeaudit, Kubescape, Conftest, Kubesec, Checkov.

***

#### 9 · Desenvolvimento Seguro de Imagens

* Evite `sudo` no `RUN`; prefira `COPY` a `ADD`.
* Fixe versões de pacotes (`apt-get install nginx=1.26.0-1`).
* Gere e valide SBOM (Syft, SPDX).
* Nunca armazene segredos em Dockerfile.
* Remova utilitários de rede (wget, curl, nc) de runtime.
* Use `.dockerignore` e multi‑stage builds com poucas camadas.
* Trabalhe com `WORKDIR` absoluto; evite `cd`.
* Não use a tag `latest`; assine imagens (Cosign, Notary v2).
* Varredura automática: **Hadolint**, **Trivy**, **Clair**, **Grype**, **Kics**.
