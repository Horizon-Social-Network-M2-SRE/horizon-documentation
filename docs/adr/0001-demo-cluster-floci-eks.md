# ADR 0001: Demo cluster on Floci EKS (k3s)

- Status: Accepted
- Date: 2026-11-21
- Deciders: Kais, Bouchiba (S1-11)
- Supersedes: plan v6 decisions 9 and 14 (minikube for the demo)

## Context

The brief requires the services to be orchestrated with Kubernetes and observed with Prometheus
and Grafana. Plan v6 chose a single-node minikube cluster for the demo, on a school or free cloud
VM, otherwise a team laptop.

[Floci](https://github.com/floci-io/floci) is a free, open-source local AWS emulator (a drop-in
replacement for LocalStack). Its EKS API creates a real k3s cluster in Docker, with a live
Kubernetes API server and a kubeconfig obtained through the standard AWS CLI. This lets the team
use the same EKS workflow as a real AWS deployment, without cloud costs.

## Decision

The demo cluster is an **EKS cluster emulated by Floci** (k3s underneath).

```bash
docker run -d --name floci -p 4566:4566 \
  -v /var/run/docker.sock:/var/run/docker.sock floci/floci:<pinned-version>
aws --endpoint-url http://localhost:4566 eks create-cluster --name horizon-demo ...
aws --endpoint-url http://localhost:4566 eks update-kubeconfig --name horizon-demo
kubectl get nodes
```

- Compose stays the local development stack (S1 to S3).
- kind stays the CI cluster for the deploy smoke test (S4-07); the Helm chart is the same.
- Helm, Traefik Ingress, kube-prometheus-stack, Sloth and the failure drill target the Floci EKS
  cluster from S4.
- The Floci setup (pinned image, cluster creation script, kubeconfig steps) lives in
  horizon-infrastructure, owned by the platform team.

## Consequences

Positive:

- EKS workflow (AWS CLI, kubeconfig, IAM) is a stronger talking point than minikube, at no cost.
- Same Kubernetes API as any cluster: Helm chart, probes, HPA and PodDisruptionBudgets unchanged.
- Runs on a team laptop with Docker; no cloud account or VM to manage.

Negative and mitigations:

| Risk | Mitigation |
| --- | --- |
| Emulated EKS, not a real AWS cluster | Ask the professor in week 1 whether it is accepted (questions file) |
| Runs on a laptop the professor cannot reach | Live demo from the laptop; optional Cloudflare Tunnel; recorded run as fallback |
| k3s needs rootful Docker (rootless setups fail on kernel resources) | Use Docker Desktop or rootful Docker on the demo machine; document it |
| kubectl rejects the `test/test` IAM key for cluster-admin | Create a real IAM key in Floci in the setup script |
| Upstream image changes (`latest`) | Pin the `floci/floci` image version; never use the deprecated `hectorvent/floci` image |
| Single node, limited resources | Requests and limits sized for one node; HPA demo with small replica counts |

Fallback (trigger: the professor refuses Floci, or Floci EKS is not stable by S4 day 3):
single-node minikube, as in plan v6.
