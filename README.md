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

Currently exploring AI infrastructure patterns: model serving pipelines, vector store backends, and the platform primitives that make AI workloads production-safe.

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
> Conversational analytics platform with an AI-powered query engine, full-stack observability, and a containerized delivery pipeline.

**Stack:** Next.js · FastAPI · PostgreSQL · Docker · Prometheus · Grafana · Loki  
**Highlights:**
- Multi-stage Docker build with Trivy scan gates in CI
- Prometheus + Grafana + Loki: metrics, dashboards, and log aggregation from day one
- CI/CD pipeline debugged to green — from container build through deployment health checks

→ [github.com/Heyyprakhar1/sentinel-ai-platform](https://github.com/Heyyprakhar1)

---

### 🔷 Terraform AWS Infrastructure
> Modular, production-oriented AWS infrastructure: 28 resources across 6 Terraform modules — designed for auto-scaling web workloads.

**Modules:** VPC · ALB · ASG · RDS · Security Groups · CloudWatch  
**Highlights:**
- State managed in S3 with DynamoDB locking
- CloudWatch alarms drive ASG scale-in/out policies
- Fully separated concerns: each module independently testable and composable

→ [github.com/Heyyprakhar1/terraform-aws-infrastructure](https://github.com/Heyyprakhar1)

---

### 🔷 Secure DevSecOps Delivery Pipeline
> End-to-end GitOps pipeline for a microservices platform — three Flask services, MySQL, Kubernetes on kind, Argo CD, and a security-scanned CI layer.

**Stack:** GitHub Actions · Argo CD · Kubernetes (kind) · Helm · Docker · ECR  
**Security gates:** Trivy (container) · Gitleaks (secrets) · Bandit (Python SAST) · Hadolint (Dockerfile lint) · pip-audit (dependency CVEs)  
**Highlights:**
- 8 reusable GitHub Actions workflow files — modular, DRY, composable
- Argo CD GitOps sync with Kubernetes manifests as the source of truth
- Secrets management without hardcoded credentials at any stage

→ [github.com/Heyyprakhar1/microservices-ecommerce-devsecops](https://github.com/Heyyprakhar1)

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
