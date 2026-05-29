<div align="center">

<img src="https://raw.githubusercontent.com/Heyyprakhar1/Heyyprakhar1/main/banner.gif" alt="Prakhar Srivastava — Platform Engineer, Cloud Infrastructure, DevSecOps" width="100%"/>

<br/>

# Building secure cloud-native systems.

**`Kubernetes`** &nbsp;·&nbsp; **`Terraform`** &nbsp;·&nbsp; **`AI Infrastructure`** &nbsp;·&nbsp; **`DevSecOps`**

<br/>

**Prakhar Srivastava** &nbsp;·&nbsp; Cloud-Native Infrastructure · Platform Engineering · DevSecOps · AI Infrastructure

[![Profile Views](https://komarev.com/ghpvc/?username=Heyyprakhar1&color=0d9373&style=flat-square&label=profile+views)](https://github.com/Heyyprakhar1)
&nbsp;
[![Blog](https://img.shields.io/badge/Hashnode-heyyprakhar01-0d9373?style=flat-square&logo=hashnode&logoColor=white)](https://heyyprakhar01.hashnode.dev)
&nbsp;
[![Portfolio](https://img.shields.io/badge/Portfolio-prakharsrivastavadevops.netlify.app-0d9373?style=flat-square&logo=netlify&logoColor=white)](https://prakharsrivastavadevops.netlify.app)

</div>

---

## About

I spent 3 years processing insurance claims at a BPO. That time wasn't wasted — I was running Linux on my personal machine since 2022, picking up Docker on weekends, building an instinct for process automation and system reliability. In March 2025, I quit. No job lined up. Just a plan I trusted.

Since then I've been building and shipping production-grade infrastructure — Kubernetes platforms, DevSecOps pipelines, modular AWS IaC — all public on GitHub. I write about what I build on Hashnode: not tutorials, more like engineering notes from someone figuring things out in public.

Open to DevOps / Platform Engineering / SRE roles at startups building in the cloud-native space.

&nbsp; **Location:** Bangalore &nbsp;|&nbsp; **Community:** [TrainWithShubham](https://github.com/TrainWithShubham) · Automation Hero

---

## Engineering Focus

```
Platform Layer         GitOps & Delivery          Observability & Security
─────────────────      ────────────────────────   ────────────────────────
Kubernetes (kind/EKS)  Argo CD · Helm             CloudWatch · Prometheus
Terraform (modular)    GitHub Actions · Jenkins   Trivy · Gitleaks · Bandit
AWS (VPC/ALB/ASG/RDS)  Docker · ECR               Hadolint · pip-audit · OPA
IAM · ECR · SNS        Ansible                    SonarCloud · RBAC
```

Design philosophy: infrastructure should be version-controlled, observable, and security-scanned before it ships — not patched after it breaks.

---

## Featured Projects

### 🔷 Sentinel AI Platform &nbsp;`flagship`

> Full-stack AI-powered DevSecOps monitoring platform. React dashboard backed by a FastAPI anomaly detection engine — deployed on Kubernetes across dev/staging/prod environments with OPA Gatekeeper policy enforcement, Prometheus + Grafana + Alertmanager observability, and Terraform-provisioned AWS EKS. Two GitHub Actions pipelines covering 8 security and quality gates end-to-end.

**Stack:** Python · FastAPI · React · Vite · Docker · Kubernetes · K3d · AWS EKS · Terraform · GitHub Actions · Prometheus · Grafana · Alertmanager · OPA Gatekeeper · SonarCloud · Trivy · Bandit · Gitleaks

→ [github.com/Heyyprakhar1/sentinel-ai-platform](https://github.com/Heyyprakhar1/sentinel-ai-platform)

---

### 🔷 Secure DevSecOps Delivery Pipeline

> End-to-end GitOps pipeline for a microservices platform — three Flask services, MySQL, Kubernetes on kind, Argo CD, and a security-scanned CI layer.

**Stack:** GitHub Actions · Argo CD · Kubernetes (kind) · Helm · Docker · ECR

**Highlights:**
- 8 reusable GitHub Actions workflow files — modular, DRY, composable
- Security gates: Trivy · Gitleaks · Bandit · Hadolint · pip-audit on every commit
- Argo CD GitOps sync with Kubernetes manifests as the source of truth
- Zero hardcoded credentials at any stage

→ [github.com/Heyyprakhar1/microservices-ecommerce-devsecops](https://github.com/Heyyprakhar1/microservices-ecommerce-devsecops)

---

### 🔷 SkillPulse &nbsp;`hackathon · TrainWithShubham`

> Three-tier application with a production-grade CI/CD pipeline, GitOps delivery via Argo CD, and a full observability stack — built under hackathon constraints.

**Stack:** Go · Nginx · MySQL · GitHub Actions · Argo CD · Kubernetes (kind) · Prometheus · Grafana · Loki

**Highlights:**
- 6-job parallel CI pipeline — image build, Trivy scan, Docker Hub push running concurrently, total runtime ~58 seconds
- Argo CD GitOps: pipeline auto-commits image SHA bumps to manifests; cluster self-syncs on every push — no `kubectl apply` in CI
- kube-prometheus-stack + Loki: metrics and log aggregation active from first deployment
- HPA validated under synthetic load — backend scales 1→4 replicas on CPU threshold
- Real Grafana dashboards: 428 MiB live memory across 3 pods from the running cluster, not mock data

→ [github.com/Heyyprakhar1/github-actions-kubernetes-masterclass](https://github.com/Heyyprakhar1/github-actions-kubernetes-masterclass)

---

### 🔷 Multi-AZ AWS Infrastructure — Terraform

> Modular, production-oriented AWS infrastructure: 28 resources across 6 Terraform modules — designed for auto-scaling web workloads across 2 availability zones.

**Modules:** VPC · ALB · ASG · RDS · Security Groups · CloudWatch

**Highlights:**
- State managed in S3 with DynamoDB locking
- Least-privilege SG chaining: ALB → EC2 → RDS — no direct external access to data tier
- CloudWatch alarms drive ASG scale-in/out policies
- 70% faster provisioning vs manual setup; zero-downtime failover validated under load

→ [github.com/Heyyprakhar1/aws-autoscaling-infra](https://github.com/Heyyprakhar1/aws-autoscaling-infra)

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

Not tutorials — engineering notes from someone figuring things out in public.

- [The app ran. The data didn't survive.](https://heyyprakhar01.hashnode.dev/the-app-ran-the-data-didn-t-survive) — what Kubernetes PVCs actually do, learned the hard way
- [Variables, Outputs, Remote State — Terraform features that matter in production](https://heyyprakhar01.hashnode.dev/variables-outputs-remote-state-and-the-terraform-features-that-actually-matter-in-production)
- [Providers, State, and Building Real AWS Infrastructure with Terraform](https://heyyprakhar01.hashnode.dev/providers-state-and-building-real-aws-infrastructure-with-terraform)
- [Infrastructure as Code with Terraform: From Concept to First Infrastructure](https://heyyprakhar01.hashnode.dev/infrastructure-as-code-iac-with-terraform-from-concept-to-first-infrastructure)

[→ All posts on Hashnode](https://heyyprakhar01.hashnode.dev)

---

## Certifications & Recognition

- **Advanced Cloud & DevOps** — Intellipaat × IIT Roorkee · iHUB DivyaSampark (2025)
- **Certified DevOps Engineer Associate** — TrainWithShubham (2025)
- **GitHub Actions & Kubernetes Masterclass** — TrainWithShubham · CertDirectory (2025)
- **Automation Hero** — TrainWithShubham #90DaysOfDevOps · recognised among 500+ engineers

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

`→` &nbsp; [Portfolio](https://prakharsrivastavadevops.netlify.app) &nbsp;·&nbsp; [Hashnode](https://heyyprakhar01.hashnode.dev) &nbsp;·&nbsp; [LinkedIn](https://www.linkedin.com/in/heyyprakhar1/)

</div>
