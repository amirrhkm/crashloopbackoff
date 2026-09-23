# Enterprise Kubernetes on AWS — a self-study lab

This is a personal, from-scratch learning project working through what it actually takes to run Kubernetes at an enterprise level — not a single "hello world" cluster, but the full surface area: networking, service mesh, GitOps delivery, traffic/DNS/certificates, storage and query performance, a real multi-protocol application, observability, and progressive delivery under load.

Everything here — manifests, infrastructure code, and the application itself — is written by hand while learning, not scaffolded or copy-pasted. Expect rough edges, dead ends, and things that get rebuilt once a better understanding sets in. That's the point.

## Curriculum

Progression roughly follows these phases, each building on the last:

1. **Setup** — local tooling, AWS safety nets
2. **Kubernetes fundamentals** — pods, deployments, services, config, probes, storage basics
3. **Networking deep-dive** — CNI, kube-proxy modes, eBPF, DNS, ingress, network policy
4. **Service mesh** — mTLS, traffic shaping, retries/circuit breaking
5. **GitOps** — Git as the source of truth for cluster state
6. **Into AWS** — a real, minimal-cost EKS cluster
7. **Traffic, load balancing, DNS & certificates** — real domain, real TLS
8. **Storage, query optimization & caching**
9. **The application** — HTTP, gRPC, and MQTT in one service, calling a public API
10. **Observability** — metrics, logs, and traces tied together
11. **Progressive delivery & resilience** — autoscaling, canary rollouts, load testing

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
infra/       cluster provisioning (eksctl / kOps / Terraform)
app/         the application built in the "application" phase
```

## Status

Actively in progress. Folders fill in as each phase is worked through — an empty phase folder just means it hasn't been reached yet.
