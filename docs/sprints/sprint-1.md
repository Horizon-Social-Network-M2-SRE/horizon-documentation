# Sprint 1: Foundations (weeks 1-2) — Milestone 2

## Goal

A user signs in from the web app against a containerised backend, with a green pipeline in every
repository.

## Exit gate

- [ ] Sign-in works from the browser against the backend running in Docker Compose
- [ ] Every code repository (backend, web, infrastructure) has a green pipeline, and every repository
      shows a visible history of small commits by its owners
- [ ] Every member has commits in at least two repositories
- [ ] Demo cluster decided (Floci EKS, [ADR 0001](../adr/0001-demo-cluster-floci-eks.md));
      making it reachable by the team is moved to a later sprint

## Scope

Register, sign in, sign out; backend skeleton and auth module; GitHub organisation with its
repositories, shared CI and Docker Compose; web shell.

## Backlog (ordered)

Snapshot from sprint planning (2026-11-21). Live status is on the GitHub Project.

Board: [GitHub Project](https://github.com/orgs/Horizon-Social-Network-M2-SRE/projects/1), Sprint = S1.

| # | Story | Repository | Owner(s) | Issue |
| --- | --- | --- | --- | --- |
| S1-03 | GitHub organisation, teams, repositories and rulesets | all | Kais | [.github#2](https://github.com/Horizon-Social-Network-M2-SRE/.github/issues/2) |
| S1-02 | Reusable CI workflows (Python and Node) — **day 1** | horizon-infrastructure | Bouchiba | [infra#1](https://github.com/Horizon-Social-Network-M2-SRE/horizon-infrastructure/issues/1) |
| S1-04 | Backend skeleton: modules, health, /metrics, Dockerfile, pytest, Mongo, Redis — **day 1** | horizon-backend | Firas, Bougui | [backend#1](https://github.com/Horizon-Social-Network-M2-SRE/horizon-backend/issues/1) |
| S1-01 | Team charter, roles, GitHub Project, Definition of Done | horizon-documentation | Kais, Firas | [doc#1](https://github.com/Horizon-Social-Network-M2-SRE/horizon-documentation/issues/1) |
| S1-05 | Commit checks: pre-commit (backend) | horizon-backend | Bouchiba | [backend#2](https://github.com/Horizon-Social-Network-M2-SRE/horizon-backend/issues/2) |
| S1-05 | Commit checks: Husky + commitlint (web) | horizon-web | Nesrine, Kais | [web#1](https://github.com/Horizon-Social-Network-M2-SRE/horizon-web/issues/1) |
| S1-06 | OpenAPI v0 (auth, users): schemas and stubs | horizon-backend | Firas | [backend#3](https://github.com/Horizon-Social-Network-M2-SRE/horizon-backend/issues/3) |
| S1-06 | Generated typed client | horizon-web | Kais, Nesrine | [web#2](https://github.com/Horizon-Social-Network-M2-SRE/horizon-web/issues/2) |
| S1-07 | auth: register with password hashing and validation | horizon-backend | Firas, Bougui | [backend#4](https://github.com/Horizon-Social-Network-M2-SRE/horizon-backend/issues/4) |
| S1-08 | auth: login, refresh, logout (JWT, Redis deny list) | horizon-backend | Bougui | [backend#5](https://github.com/Horizon-Social-Network-M2-SRE/horizon-backend/issues/5) |
| S1-09 | Docker Compose local stack, make up, make test | horizon-infrastructure | Kais (Bouchiba reviews; reassigned 2026-11-23) | [infra#2](https://github.com/Horizon-Social-Network-M2-SRE/horizon-infrastructure/issues/2) |
| S1-10 | Web shell: Next.js, sign-in and register pages, authenticated layout | horizon-web | Nesrine | [web#3](https://github.com/Horizon-Social-Network-M2-SRE/horizon-web/issues/3) |
| S1-11 | Demo cluster and questions to the professor | horizon-documentation | Kais, Bouchiba | [doc#3](https://github.com/Horizon-Social-Network-M2-SRE/horizon-documentation/issues/3) |

Unfinished stories carry over first in S2.

## Dependencies

```text
S1-02 reusable CI ──────> green pipelines in the code repositories
S1-04 skeleton ──┬──> S1-08 login/logout ───────────────────────────────┐
                 ├──> S1-06 OpenAPI v0 ──> S1-07 register ───────────────┤
                 │                    └──> S1-06 typed client ──> S1-10 ┴──> sign-in demo
S1-09 Compose (api + web + MongoDB + Redis) ──────────────────────────────┘
```

## Main risk

Pipeline work blocks everyone, so S1-02 and S1-04 start on day 1 and are reviewed first.
The OpenAPI stubs (S1-06) are merged before the web app needs them.

## Ceremonies

| Day | Ceremony | Output |
| --- | --- | --- |
| 1 | Sprint planning (1 hour) | This file, issues assigned, board in Ready |
| Daily | Asynchronous stand-up in Discord | Yesterday, today, blockers |
| Weekly | Check-in (15 minutes) | Board review, contributor activity per member and per repository |
| 6 | Scope freeze | No new stories; cut or carry over |
| 8 | Scripted demo rehearsal | Demo script works end to end on Compose |
| 10 | Sprint review = Milestone 2 presentation, then retrospective | Review notes, 2-3 actions that become S2 stories |

Progress is measured as stories done against stories planned (no story points).

## Milestone 2 presentation outline

1. Sprint goal and whether it was met
2. Stories planned against done
3. Live demo: register, sign in, sign out from the browser against the containerised backend
4. Engineering practice: organisation, rulesets, CI, commit history per member and per repository
5. Challenges, with links to ADRs (Floci EKS, Istio)
6. Next sprint (S2: profiles and connections)

## Review and retrospective

To be filled on day 10.
