# Progress

## Current position

- Phase: 00 — Ground Rules & Environment
- Status: repo, README, and tooling reference docs are in place. AWS `personal` profile is authenticated. `kubectl`, `helm`, and `kops` are already installed; `kind` is not yet installed, and the profile has no default region set. AWS Budget alarm walkthrough was given but not yet confirmed as created.
- Next action: confirm the AWS Budget alarm exists, install `kind`, set a default region on the `personal` profile, then create a local `kind` cluster and confirm `kubectl get nodes` — that closes out Phase 00 and moves into Phase 01 (Pod lifecycle).

## Session log

(most recent first)

### 2026-09-23
- Decided: stay on AWS (not Azure) to build depth on fundamentals first
- Decided: kOps over EKS for Phase 05 — updated curriculum artifact, `docs/00-setup/tools.md`, and README accordingly
- Decided: GHCR over Docker Hub for publishing the app image in Phase 08
- Wrote `docs/00-setup/tools.md` — lecture notes on kubectl, Helm, kind, kOps, eksctl, aws CLI, each with an ASCII diagram of where it actually executes
- Confirmed locally installed: `kubectl` v1.35.3, `helm` v4.1.3, `kops` v1.35.0. Confirmed `aws sts get-caller-identity --profile personal` resolves correctly. `kind` and a region on the profile are still outstanding.
- Set up the repo (`crashloopbackoff`), README, `.gitignore`, and folder structure (`docs/`, `manifests/`, `infra/`, `app/`)
