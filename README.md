# Enterprise Kubernetes on AWS — a self-study lab

## Tech stack

**Cloud & provisioning**

![AWS](https://img.shields.io/badge/AWS-EC2%20·%20IAM%20·%20Budgets-232F3E?style=for-the-badge)
![kOps](https://img.shields.io/badge/kOps-self--managed%20control%20plane-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![kind](https://img.shields.io/badge/kind-local%20dev-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-reference-844FBA?style=for-the-badge&logo=terraform&logoColor=white)
![eksctl](https://img.shields.io/badge/eksctl-reference-232F3E?style=for-the-badge)

**Kubernetes core & tooling**

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![kubectl](https://img.shields.io/badge/kubectl-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)

**Containers & registry**

![Docker](https://img.shields.io/badge/Docker%2FOCI-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GHCR](https://img.shields.io/badge/GHCR-181717?style=for-the-badge&logo=github&logoColor=white)

**Networking**

![CNI](https://img.shields.io/badge/CNI-4A4A4A?style=for-the-badge)
![eBPF](https://img.shields.io/badge/eBPF-000000?style=for-the-badge)
![kube--proxy](https://img.shields.io/badge/kube--proxy-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![DNS](https://img.shields.io/badge/DNS-4A4A4A?style=for-the-badge)
![Ingress](https://img.shields.io/badge/Ingress-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![NetworkPolicy](https://img.shields.io/badge/NetworkPolicy-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)

**Service mesh** _(specific mesh TBD)_

![mTLS](https://img.shields.io/badge/mTLS-6E56CF?style=for-the-badge)
![Traffic Shaping](https://img.shields.io/badge/Traffic%20Shaping-6E56CF?style=for-the-badge)
![Circuit Breaking](https://img.shields.io/badge/Circuit%20Breaking-6E56CF?style=for-the-badge)

**GitOps** _(tool TBD)_

![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitOps](https://img.shields.io/badge/GitOps-F05032?style=for-the-badge)

**Traffic, DNS & certificates**

![Load Balancing](https://img.shields.io/badge/Load%20Balancing-0A66C2?style=for-the-badge)
![TLS](https://img.shields.io/badge/TLS%2FACME-0A66C2?style=for-the-badge&logo=letsencrypt&logoColor=white)
![DNS](https://img.shields.io/badge/DNS-0A66C2?style=for-the-badge)

**Storage & data**

![Persistent Volumes](https://img.shields.io/badge/Persistent%20Volumes-047857?style=for-the-badge&logo=kubernetes&logoColor=white)
![Query Optimization](https://img.shields.io/badge/Query%20Optimization-047857?style=for-the-badge)
![Caching](https://img.shields.io/badge/Caching-047857?style=for-the-badge)

**Application protocols**

![HTTP](https://img.shields.io/badge/HTTP-005571?style=for-the-badge)
![gRPC](https://img.shields.io/badge/gRPC-4285F4?style=for-the-badge)
![MQTT](https://img.shields.io/badge/MQTT-660066?style=for-the-badge&logo=mqtt&logoColor=white)

**Observability** _(stack TBD)_

![Metrics](https://img.shields.io/badge/Metrics-E6522C?style=for-the-badge)
![Logs](https://img.shields.io/badge/Logs-E6522C?style=for-the-badge)
![Traces](https://img.shields.io/badge/Traces-E6522C?style=for-the-badge)

**Progressive delivery**

![Autoscaling](https://img.shields.io/badge/Autoscaling-D97706?style=for-the-badge&logo=kubernetes&logoColor=white)
![Canary Rollouts](https://img.shields.io/badge/Canary%20Rollouts-D97706?style=for-the-badge)
![Load Testing](https://img.shields.io/badge/Load%20Testing-D97706?style=for-the-badge)

This is a personal, from-scratch learning project working through what it actually takes to run Kubernetes at an enterprise level — not a single "hello world" cluster, but the full surface area: networking, service mesh, GitOps delivery, traffic/DNS/certificates, storage and query performance, a real multi-protocol application, observability, and progressive delivery under load.

Everything here — manifests, infrastructure code, and the application itself — is written by hand while learning, not scaffolded or copy-pasted. Expect rough edges, dead ends, and things that get rebuilt once a better understanding sets in. That's the point.

## Curriculum

Progression roughly follows these phases, each building on the last:

1. **Setup** — local tooling, AWS safety nets
2. **Kubernetes fundamentals** — pods, deployments, services, config, probes, storage basics
3. **Networking deep-dive** — CNI, kube-proxy modes, eBPF, DNS, ingress, network policy
4. **Service mesh** — mTLS, traffic shaping, retries/circuit breaking
5. **GitOps** — Git as the source of truth for cluster state
6. **Into AWS** — a real, minimal-cost, self-managed cluster (kOps on EC2), chosen over a managed service specifically to see the control plane instead of having it hidden
7. **Traffic, load balancing, DNS & certificates** — real domain, real TLS
8. **Storage, query optimization & caching**
9. **The application** — HTTP, gRPC, and MQTT in one service, calling a public API, containerized and published to a registry (GHCR)
10. **Observability** — metrics, logs, and traces tied together
11. **Progressive delivery & resilience** — autoscaling, canary rollouts, load testing

## Key decisions

Updated as decisions are actually made, not just planned:

- **Cloud: AWS**, not Azure — staying put to build depth on fundamentals rather than re-deriving cloud-specific setup elsewhere
- **Cluster provisioning: kOps**, not EKS — kOps runs the control plane on plain EC2, SSH-able, with etcd/kube-apiserver/kube-scheduler visible as real processes; EKS hides all of that behind a managed service, and seeing the control plane is the actual goal of that phase
- **Container registry: GHCR**, not Docker Hub — lives next to this repo (same account, free for public images), no separate account to manage

Reasoning for decisions not yet reached (service mesh, GitOps tool, application language) lives in the phase docs once each phase is actually worked through.

## Cost & safety guardrails

This is a personal-budget project, not a company AWS account, so cost control is a first-class concern:

- All AWS work runs under a dedicated `personal` profile
- A monthly AWS Budget with tiered alerts (33% actual / 100% actual / 100% forecasted) is in place before any billable resource gets created
- Every session that touches real AWS ends with a teardown pass — clusters, load balancers, and volumes are not left running between sessions
- Most of the curriculum (fundamentals, networking, mesh, GitOps) runs entirely locally at zero cost; AWS only enters the picture where the concept genuinely requires it

## Structure

```
docs/        notes and write-ups, one folder per phase
manifests/   Kubernetes YAML
infra/       cluster provisioning (kOps primarily / eksctl / Terraform)
app/         the application built in the "application" phase
```

## Status

Actively in progress. Folders fill in as each phase is worked through — an empty phase folder just means it hasn't been reached yet.
