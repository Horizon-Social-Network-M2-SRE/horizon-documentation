# Decisions log

Closed decisions, each with a fallback and the condition that triggers it. Nobody reopens a
decision without evidence; a change is recorded here and, when it is architectural, as an ADR.

Source: plan v6, section 3 (updated 18 Nov 2026), plus later changes marked with a date.

| # | Decision | Fallback and trigger |
| --- | --- | --- |
| 1 | Backend: Python + FastAPI modular monolith (auth, users, connections, posts, feed, interactions, notifications), Pydantic, PyMongo async | A module becomes a service only through an ADR |
| 2 | Background jobs: Celery with Redis broker, one worker Deployment from the backend image | Fan-out inside the api process if Celery is not stable by S3 day 3 |
| 3 | Web: Next.js (App Router), TypeScript, TanStack Query, Tailwind | — |
| 4 | Mobile: mobile-first layouts + optional installable PWA | Cut the PWA |
| 5 | Data: MongoDB, one collection per module, no MySQL | — |
| 6 | Auth: OAuth2 password flow, JWT ~15 min, refresh token and deny list in Redis | Plain JWT if Redis auth slips past S1 |
| 7 | Real time: FastAPI WebSocket + Redis pub/sub + since cursor | Short polling; Redis Streams only if S3 shows dropped events |
| 8 | Repositories: horizon-web, horizon-backend, horizon-infrastructure, horizon-documentation, plus .github | One repository only if the professor accepts in writing |
| 9 | Orchestration: Compose locally, kind in CI, **Floci EKS (k3s) for the demo** *(changed 2026-11-21, [ADR 0001](adr/0001-demo-cluster-floci-eks.md))* | minikube if the professor refuses Floci or it is not stable by S4 day 3 |
| 10 | Ingress: Traefik with standard Ingress resources | — |
| 11 | Service mesh: none planned | Istio minimal profile in the S5 buffer if required |
| 12 | Deployment: one generic Helm chart; a release opens an image-tag PR in infrastructure; helm upgrade on merge | Argo CD only as a stretch |
| 13 | Merge method: rebase and merge | — |
| 14 | Demo cluster: **Floci EKS on a team laptop with rootful Docker** *(changed 2026-11-21, ADR 0001)* | minikube; recorded run if no machine is available |
| 15 | Planning tool: one organisation-level GitHub Project spanning all repositories (Trello mirrors it in S1) | — |
| 16 | Organisation: Horizon-Social-Network-M2-SRE, two owners, teams backend/web/platform, `protect-main` ruleset per repository, public repositories *(updated 2026-11-21: per-repository ruleset, repositories made public for the Free plan)* | Private repositories with GitHub Education benefits |

## Answers from the professor

Questions sent in week 1: see [questions-for-the-professor.md](questions-for-the-professor.md).

| Date | Question | Answer | Impact |
| --- | --- | --- | --- |
| | | | |
