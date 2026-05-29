<div align="center">

<img src="https://raw.githubusercontent.com/Heyyprakhar1/Heyyprakhar1/main/banner.gif" alt="Prakhar Srivastava — Platform Engineer, Cloud Infrastructure, DevSecOps" width="100%"/>

<br/>

# Building secure cloud-native systems.

**`Kubernetes`** &nbsp;·&nbsp; **`Terraform`** &nbsp;·&nbsp; **`AI Infrastructure`** &nbsp;·&nbsp; **`DevSecOps`**

<br/>

**Prakhar Srivastava** &nbsp;·&nbsp; Cloud-Native Infrastructure · Platform Engineering · DevSecOps · AI Infrastructure

[![Profile Views](https://komarev.com/ghpvc/?username=Heyyprakhar1&color=0d9373&style=flat-square&label=profile+views)](https://github.com/Heyyprakhar1)
&nbsp;
[![Blog](https://img.shields.io/badge/Hashnode-heyyprakhar01-0d9373?style=flat-square&logo=hashnode&logoColor=white)](https://hashnode.com/@heyyprakhar01)
&nbsp;
[![Portfolio](https://img.shields.io/badge/Portfolio-prakharsrivastava--devops.netlify.app-0d9373?style=flat-square&logo=netlify&logoColor=white)](https://prakharsrivastava-devops.netlify.app)

</div>

---

## About

Infrastructure engineer with a focus on cloud-native systems, platform automation, and secure delivery workflows. I work at the intersection of Kubernetes-native tooling, GitOps, and DevSecOps — designing systems that are observable by default, auditable end-to-end, and built to scale without accumulating operational debt.

Currently building AI infrastructure patterns: model serving pipelines, vector store backends, and the platform primitives that make AI workloads production-safe.

Open to platform engineering, SRE, and DevSecOps roles at startups building in the cloud-native space.

&nbsp; **Location:** Bangalore &nbsp;|&nbsp; **Community:** [TrainWithShubham](https://github.com/TrainWithShubham) · Automation Hero

---

## Engineering Focus

```
Platform Layer         GitOps & Delivery          Observability & Security
─────────────────      ────────────────────────   ────────────────────────
Kubernetes (kind/EKS)  Argo CD · Helm             CloudWatch · Prometheus
Terraform (modular)    GitHub Actions · Jenkins   Trivy · Gitleaks · Bandit
AWS (VPC/ALB/ASG/RDS)  Docker · ECR               Hadolint · pip-audit
IAM · DynamoDB · SNS   Ansible                    IAM Policies · RBAC
```

Design philosophy: infrastructure should be version-controlled, observable, and security-scanned before it ships — not patched after it breaks.

---

## Featured Projects

### 🔷 Sentinel AI Platform &nbsp;`flagship`

> AI-powered DevSecOps monitoring platform — full-stack cloud-native system with a React dashboard, FastAPI AI backend, multi-environment Kubernetes deployment, OPA policy enforcement, Prometheus observability stack, and Terraform-provisioned AWS EKS infrastructure. Every layer production-engineered: security-scanned CI, non-root containers, HPA, PDB, NetworkPolicy, and Alertmanager wired to Slack.

**Backend:** Python 3.12 · FastAPI · Uvicorn · psutil · pydantic-settings  
**Frontend:** React · Vite · Nginx (multi-stage Docker)  
**Containerization:** Docker (multi-stage, non-root, health-checked) · Docker Compose  
**Orchestration:** Kubernetes · K3d (local) · AWS EKS v1.35 (Terraform-provisioned)  
**IaC:** Terraform — VPC · EKS · ECR · IAM (ap-south-1, t3.medium nodes)  
**CI/CD:** GitHub Actions — 2 pipelines, 8 jobs  
**DevSecOps:** SonarCloud · Trivy · Bandit · pip-audit · npm audit · Hadolint · ShellCheck · Gitleaks · OPA Gatekeeper  
**Observability:** Prometheus · Grafana · Alertmanager (PrometheusRule + ServiceMonitor + Slack routing)

---

**Architecture — Production (AWS EKS):**
```
GitHub Push
    ↓
GitHub Actions CI (test → sonarcloud → docker-build → trivy scan)
    ↓
GitHub Actions Security (bandit → pip-audit → npm audit → hadolint → shellcheck → gitleaks)
    ↓
Amazon ECR (scan-on-push, 10-image lifecycle policy)
    ↓
AWS EKS v1.35 — ap-south-1 (Terraform: VPC + public/private subnets + IGW)
    ↓
┌──────────────────────────────────────────────────────┐
│  Kubernetes Manifests (kustomize base + overlays)    │
│                                                      │
│  sentinelai-dev    sentinelai-staging  sentinelai-prod│
│  1 replica         2 replicas          3 replicas    │
│  50m/64Mi          100m/128Mi          200m/256Mi    │
│  DEBUG             INFO                WARNING       │
└──────────────────────────────────────────────────────┘
    ↓
OPA Gatekeeper (3 constraint templates: ban :latest, require non-root, require resource limits)
    ↓
HPA (CPU 70% / Memory 80% → 2–10 replicas) + PDB (minAvailable: 1)
    ↓
NetworkPolicy (ingress from sentinelai-dev + monitoring NS only; egress to Prometheus :9090 + DNS)
    ↓
Prometheus (ServiceMonitor scraping /metrics every 15s) + Grafana + Alertmanager
    ↓
PrometheusRules: SentinelAIHighCPU (>80%, 2m) · SentinelAIHighMemory (>85%, 2m) · SentinelAIDown (1m)
    ↓
Slack: #sentinelai-alerts (warning) · #sentinelai-critical (critical)
```

---

**What's actually built:**

**AI Anomaly Detection Engine**
- `AnomalyDetector` class using Z-score statistical analysis against a 20-reading rolling buffer
- Detects CPU and memory anomalies with severity classification: `normal → warning → critical`
- Confidence scoring: `low / medium / high` mapped to Z-score thresholds (2.0 / 3.0)
- Warms up after 5 readings — no false positives on cold start
- Powers `/recommendation` endpoint with actionable remediation text (HPA scale-up suggestions, memory leak flags)

**Full-Stack Dashboard (React + Vite)**
- Real-time polling architecture: health (10s) · status (15s) · alerts (5s) · recommendations (5s)
- Components: `MetricCard` · `MetricsChart` (30-point rolling history) · `AlertsFeed` · `AnomalyPanel` · `K8sPanel` · `StatusBar` · `StatusDetails`
- Nginx-served in production via multi-stage Docker build; `Dockerfile.compose` variant for local Docker Compose

**Dual Docker Compose Stack (local)**
- 5-service stack: FastAPI backend · React/Nginx frontend · Prometheus · Grafana · Alertmanager
- Backend health-checked (`/health` probe with retry) before frontend starts
- Grafana with persistent volume, admin credentials from `.env`, sign-up disabled

**CI/CD — 2 Pipelines, 8 Jobs:**

| Pipeline | Job | What It Does |
|---|---|---|
| `ci.yml` | `test` | pytest + coverage (≥70% gate) |
| `ci.yml` | `sonarcloud` | SonarCloud SAST (after test passes) |
| `ci.yml` | `docker-build` | Build image + Trivy CRITICAL scan (exit 1 on fail) |
| `security.yml` | `python-security` | Bandit (Python SAST) + pip-audit (CVE check) |
| `security.yml` | `js-security` | npm audit (high severity gate) on frontend |
| `security.yml` | `dockerfile-lint` | Hadolint on all 3 Dockerfiles |
| `security.yml` | `shell-check` | ShellCheck on all scripts/ |
| `security.yml` | `secret-scan` | Gitleaks full history scan |

**OPA Gatekeeper — 3 Policy Templates (Rego):**
- `BanLatestTag` — blocks any container using `:latest` image tag at admission
- `RequireNonRoot` — enforces `securityContext.runAsNonRoot: true` on all containers
- `RequireResourceLimits` — rejects pods without CPU/memory limits defined

**Terraform IaC (ap-south-1):**
- VPC: 10.0.0.0/16 · 2 public subnets (ap-south-1a/1b) · 2 private subnets · IGW · route tables
- EKS: v1.35 cluster · t3.medium node group (1–3 nodes) · API auth mode · IAM roles (cluster + node group) with AmazonEKSClusterPolicy, AmazonEKSWorkerNodePolicy, AmazonEKS_CNI_Policy, AmazonEC2ContainerRegistryReadOnly
- ECR: scan-on-push enabled · lifecycle policy (keep last 10 images) · S3 + DynamoDB state backend

**API Surface:**

| Endpoint | Method | Purpose | Kubernetes Binding |
|---|---|---|---|
| `/health` | GET | App liveness + version info | Liveness probe |
| `/status` | GET | Uptime + readiness check | Readiness probe |
| `/metrics` | GET | Prometheus metrics | ServiceMonitor scrape target (15s) |
| `/alerts` | GET | Live alert feed | Core workload |
| `/recommendation` | GET | AI anomaly analysis + remediation | Core workload |

→ [github.com/Heyyprakhar1/sentinel-ai-platform](https://github.com/Heyyprakhar1/sentinel-ai-platform)

---

### 🔷 Terraform AWS Infrastructure

> Modular, production-oriented AWS infrastructure: 28 resources across 6 Terraform modules — designed for auto-scaling web workloads.

**Modules:** VPC · ALB · ASG · RDS · Security Groups · CloudWatch

**Highlights:**
- State managed in S3 with DynamoDB locking
- CloudWatch alarms drive ASG scale-in/out policies
- Fully separated concerns: each module independently testable and composable

→ [github.com/Heyyprakhar1/aws-autoscaling-infra](https://github.com/Heyyprakhar1/aws-autoscaling-infra)

---

### 🔷 Secure DevSecOps Delivery Pipeline

> End-to-end GitOps pipeline for a microservices platform — three Flask services, MySQL, Kubernetes on kind, Argo CD, and a security-scanned CI layer.

**Stack:** GitHub Actions · Argo CD · Kubernetes (kind) · Helm · Docker · ECR

**Security gates:** Trivy (container) · Gitleaks (secrets) · Bandit (Python SAST) · Hadolint (Dockerfile lint) · pip-audit (dependency CVEs)

**Highlights:**
- 8 reusable GitHub Actions workflow files — modular, DRY, composable
- Argo CD GitOps sync with Kubernetes manifests as the source of truth
- Secrets management without hardcoded credentials at any stage

→ [github.com/Heyyprakhar1/microservices-ecommerce-devsecops](https://github.com/Heyyprakhar1/microservices-ecommerce-devsecops)

---

### 🔷 SkillPulse &nbsp;`hackathon · TrainWithShubham`

> Three-tier application with a production-grade CI/CD pipeline, GitOps delivery via Argo CD, and a full observability stack — built under hackathon constraints.

**Stack:** Go · Nginx · MySQL · GitHub Actions · Argo CD · Kubernetes (kind) · Prometheus · Grafana · Loki

**Situation:** The TrainWithShubham GitHub Actions & Kubernetes Masterclass hackathon required participants to ship a real application with a real, end-to-end automated pipeline — not a demo, not a script, but a system where a `git push` becomes a live deployment with no human in the loop.

**Task:** Design and deliver a three-tier app (Go backend, Nginx-served frontend, MySQL) with a CI pipeline that builds, tags, and pushes container images, a CD pipeline that deploys to Kubernetes via GitOps, and an observability layer covering metrics, logs, and dashboards — all wired together and running under time pressure.

**Action:**
- Built a 6-job parallel CI pipeline in GitHub Actions: image build, security scan (Trivy), and Docker Hub push running concurrently — total pipeline time under 60 seconds
- Implemented GitOps CD with Argo CD: pipeline auto-commits image SHA bumps to manifests; cluster self-syncs on every push without `kubectl apply` in CI
- Deployed kube-prometheus-stack via Argo CD for metrics (Prometheus + Grafana) and loki-stack for log aggregation (Promtail DaemonSet → Loki) — observability active from first deployment
- Wired HPA on the backend Deployment: scales 1→4 replicas on CPU threshold, validated under synthetic load
- Wrote idempotent deploy scripts and `.env` guard checks so the pipeline fails loudly and cleanly on misconfiguration rather than silently breaking production

**Result:** Full pipeline green — CI builds in ~58 seconds, Argo CD syncs within seconds of a push, all three Argo CD apps (skillpulse, monitoring, loki-stack) held Healthy + Synced throughout. Real Grafana dashboards showing 428 MiB live memory across 3 pods from the running cluster — not mock data.

→ [github.com/Heyyprakhar1/github-actions-kubernetes-masterclass](https://github.com/Heyyprakhar1/github-actions-kubernetes-masterclass)

---

## Tech Stack

**Cloud & Infrastructure**

![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=flat-square&logo=helm&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=flat-square&logo=ansible&logoColor=white)

**CI/CD & GitOps**

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![Argo CD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=flat-square&logo=argo&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)

**Observability & Security**

![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=flat-square&logo=aquasecurity&logoColor=white)

---

## Technical Writing

Writing about things I've actually built and debugged — not summarized from docs.

**AWS for Absolute Beginners** — [Hashnode series](https://hashnode.com/@heyyprakhar01)
- Part 1: EC2, IAM, core services — what they do and how they connect
- Part 2: VPC deep dive — networking, CIDR, subnets, route tables

Topics in progress: Kubernetes networking internals · Terraform module design patterns · DevSecOps pipeline architecture

---

## Certifications & Recognition

- **Advanced Cloud & DevOps** — Intellipaat × IIT Roorkee (2025)
- **Automation Hero** — TrainWithShubham DevOps Community
- **#90DaysOfDevOps** — completed, documented, shipped

---

## GitHub Activity

<div align="center">

![GitHub Streak](https://streak-stats.demolab.com?user=Heyyprakhar1&hide_border=true&background=0d1117&ring=0d9373&fire=0d9373&currStreakLabel=9fe1cb&sideLabels=9fe1cb&dates=888780&currStreakNum=9fe1cb&sideNums=9fe1cb)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=Heyyprakhar1&layout=donut-vertical&hide_border=true&bg_color=0d1117&text_color=9fe1cb&title_color=0d9373&langs_count=6&hide=html,css,scss,dockerfile&card_width=280)

</div>

```
  624 contributions  ·  Dec 2024 – present  ·  HCL · Go · Python · YAML · Shell
```

---

<div align="center">

`→` &nbsp; [Portfolio](https://prakharsrivastava-devops.netlify.app) &nbsp;·&nbsp; [Hashnode](https://hashnode.com/@heyyprakhar01) &nbsp;·&nbsp; [LinkedIn](https://www.linkedin.com/in/heyyprakhar1/)

</div>
