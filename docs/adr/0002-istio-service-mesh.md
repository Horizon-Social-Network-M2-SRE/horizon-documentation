# ADR 0002: Istio service mesh

- Status: Accepted
- Date: 2026-11-21
- Deciders: Kais, Bouchiba (S1-11, after the professor's answers)
- Supersedes: plan v6 decision 11 (no service mesh)

## Context

The brief lists Istio, Prometheus and Grafana for observability. Plan v6 left the mesh out and
kept Istio as a late fallback. In week 1 the team decided to run Istio, so it moves out of the
scope cut order and into the plan.

The demo cluster is a single-node Floci EKS cluster (k3s, [ADR 0001](0001-demo-cluster-floci-eks.md)),
so the mesh must stay light.

## Decision

- Install Istio with the **minimal profile** (istiod only) through Helm, from horizon-infrastructure.
- Enable sidecar injection on the `horizon` namespace (web, api, worker). MongoDB and Redis
  StatefulSets stay outside the mesh to keep the single node light.
- **Traefik stays the ingress** (decision 10). Istio handles traffic between services.
- Use the mesh for what we can show and measure:
  - mTLS between web, api and worker (`PeerAuthentication` in STRICT mode)
  - Istio request metrics (`istio_requests_total`, `istio_request_duration_milliseconds`) scraped
    by kube-prometheus-stack, as an extra SLI source next to the application metrics
  - retries and timeouts in a `VirtualService` for the api (S5-07)
  - optional Kiali for the service graph in the demo
- Planning: install with the Helm chart work in S4 (S4-06 / S4-09), tuned in S5.

## Consequences

Positive: matches the brief's tooling list; mTLS, retries and mesh metrics are SRE talking points.

Negative and mitigations:

| Risk | Mitigation |
| --- | --- |
| Sidecars use CPU and memory on a single node | Minimal profile, small sidecar requests, data stores outside the mesh |
| WebSocket and Traefik routing break through the mesh | Test `/ws` through Traefik and the sidecar in S4; port naming `http-*` on Services |
| More moving parts for the failure drill | Rehearse the drill with the mesh on kind first (S4-11) |
| Learning cost | Pair Bouchiba with one backend member on the first install |

Fallback (trigger: sidecars do not fit on the single node by S4 day 6): Istio ambient mode
(ztunnel, no sidecars).
