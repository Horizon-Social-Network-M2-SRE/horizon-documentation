# Team charter

## Mission

Build Horizon Social Network in five two-week sprints, graded mainly on engineering practice:
small and frequent commits by every member, green pipelines, containerised services, Kubernetes
deployment and measurable reliability (SLIs, SLOs, error budgets).

## Team and roles

Roles are a starting point, not a wall. Everyone commits their own work every week, reviews code
outside their own layer, and ships tests and metrics with each backend feature.

| Member | GitHub | Role | Main repositories | Also reviews |
| --- | --- | --- | --- | --- |
| Kais | @Kaisoueriemmi | Scrum master; web co-lead (connections, interactions); documentation | horizon-web, horizon-documentation | horizon-backend, horizon-infrastructure |
| Bouchiba | @bouchiba43 | SRE and platform lead | horizon-infrastructure | horizon-backend, horizon-web |
| Firas | @firas-ben-said | Backend lead (auth, users, connections, posts) | horizon-backend | horizon-infrastructure, horizon-web |
| Bougui | @mohamedamine596 | Backend lead (feed, WebSocket, interactions) | horizon-backend | horizon-infrastructure, horizon-web |
| Nessrine | @NesrineBousrih | Web app lead | horizon-web | horizon-backend, horizon-infrastructure |

GitHub teams: `backend` (Firas, Bougui), `web` (Nessrine, Kais), `platform` (Bouchiba, Kais).
Organisation owners: Kais, Bouchiba and Firas.

### Scrum master duties

- Owns the backlog and the organisation-level GitHub Project.
- Runs sprint planning, the weekly check-in, the review and the retrospective.
- Publishes the weekly contributor report and the Monday list of stale pull requests.
- Keeps the decisions log and the risks list up to date.

## Working agreements

1. **Commit your own work, every week.** Under your own GitHub account. When pairing, credit the
   partner with a `Co-authored-by:` trailer.
2. **Two repositories minimum.** Every member commits to at least two repositories, and every
   repository shows at least two authors.
3. **Small and continuous.** One issue per branch, pull requests under about 300 lines, merged
   within about two days.
4. **Cross-layer review.** Nobody is the only reviewer of their own layer. Review turnaround
   target: 24 hours.
5. **Contract first.** An endpoint is agreed in OpenAPI before the web app uses it.
6. **AI is a drafting tool.** A human reads, tests and understands AI output before merging, and
   the pull request says when AI helped. Anyone may be asked to explain any line they merged.
7. **No reopening closed decisions without evidence.** See the [decisions log](decisions-log.md).
8. **Blockers are raised early.** A blocker older than half a day goes to Discord with `@here`.

## Communication

| Channel | Use |
| --- | --- |
| Discord `#standup` | Asynchronous daily stand-up: yesterday, today, blockers |
| Discord `#dev` | Technical questions, pairing requests |
| GitHub issues and pull requests | Every decision about code; linked to the Project |
| GitHub Project | Single source of truth for the plan (Trello mirrors it during S1) |
| horizon-documentation | Charter, process, ADRs, decisions, sprint notes |

## Cadence

| When | What | Owner |
| --- | --- | --- |
| Day 1, 1 hour | Sprint planning: goal, backlog, owners | Scrum master |
| Daily, 5 minutes | Asynchronous stand-up in Discord | Whole team |
| Weekly, 15 minutes | Check-in: board, contributor activity per member and per repository | Scrum master |
| Every Monday | Stale pull request list | Scrum master |
| Every sprint | Explain-it round: a random member walks through a recent pull request | Scrum master |
| Day 6 | Scope freeze | Whole team |
| Day 8 | Scripted demo rehearsal on the deployed environment | Whole team |
| Day 10, 45 minutes | Sprint review (milestone presentation), then retrospective | Whole team |

No story points: progress is measured as stories done against stories planned.

## Conflict resolution

Technical disagreements are settled with evidence (a spike, a benchmark, a prototype) and recorded
as an ADR. If the team still disagrees after one discussion, the lead of the affected layer
decides, and the scrum master records the decision.
