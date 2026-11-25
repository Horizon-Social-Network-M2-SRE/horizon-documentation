# horizon-documentation

Planning, process and design documentation for **Horizon Social Network**, the M2 integration
project (software development, DevOps and SRE).

Horizon is a small social network for the Horizon community (students, staff and teachers):
profiles, sign-in, search, connections, plain-text posts, a near-real-time news feed, likes,
shares and comments.

## Repositories

| Repository | Contents | Owners |
| --- | --- | --- |
| [horizon-backend](https://github.com/Horizon-Social-Network-M2-SRE/horizon-backend) | FastAPI modular backend and Celery worker | Firas, Bougui |
| [horizon-web](https://github.com/Horizon-Social-Network-M2-SRE/horizon-web) | Next.js web app (mobile-first, optional PWA) | Nessrine, Kais |
| [horizon-infrastructure](https://github.com/Horizon-Social-Network-M2-SRE/horizon-infrastructure) | Reusable CI, Compose, Helm, observability, SLOs, runbooks | Bouchiba |
| horizon-documentation (this repository) | Charter, process, ADRs, decisions, sprint notes | Kais |
| [.github](https://github.com/Horizon-Social-Network-M2-SRE/.github) | Organisation profile, shared issue and pull request templates, org setup script | Kais |

## Contents

| Path | What it holds |
| --- | --- |
| [docs/team-charter.md](docs/team-charter.md) | Team, roles, working agreements, communication, cadence |
| [docs/process/definition-of-ready-and-done.md](docs/process/definition-of-ready-and-done.md) | Definition of Ready and Definition of Done |
| [docs/process/commits-and-reviews.md](docs/process/commits-and-reviews.md) | Branches, Conventional Commits, pull requests, reviews |
| [docs/process/github-project.md](docs/process/github-project.md) | Organisation-level GitHub Project: fields, views, issue hierarchy |
| [docs/decisions-log.md](docs/decisions-log.md) | Closed decisions with fallbacks, answers from the professor |
| [docs/adr/](docs/adr/) | Architecture decision records (Floci EKS demo cluster, Istio) |
| [docs/questions-for-the-professor.md](docs/questions-for-the-professor.md) | Week 1 questions to the professor |

The full project plan lives in the shared Google Doc *Horizon Social Network — Project Planning
Document*. This repository holds the parts that change with the code and must stay versioned.

## Contributing

Same rules as every Horizon repository: one issue per branch, Conventional Commits with the
issue number, a pull request reviewed by someone outside your layer. See
[docs/process/commits-and-reviews.md](docs/process/commits-and-reviews.md).
