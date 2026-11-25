# Organisation-level GitHub Project

One GitHub Project, owned by the organisation, plans the whole team's work across all
repositories. The Trello board mirrors it during S1 and is retired once the Project is in use.

## Issue hierarchy

| Level | GitHub object | Example |
| --- | --- | --- |
| Epic | Parent issue (label `epic`) | Auth and Profiles |
| Story | Child issue (label `story`) with acceptance criteria | S1-07 auth: register with password hashing |
| Task | Sub-issue or checklist item, finishable in under a day | Add argon2 hasher |

Each issue lives in the repository whose code it changes. A cross-repository story (for example
S1-06, OpenAPI draft and generated client) has one parent issue and one child per repository.

## Epics

Foundations and Platform · Auth and Profiles · Connections · Posts and Feed · Interactions ·
Web App · Observability · SRE

## Fields

| Field | Type | Values |
| --- | --- | --- |
| Status | Single select | Backlog, Ready, In progress, In review, Done |
| Sprint | Single select | S1 to S5 |
| Epic | Single select | The eight epics above |
| Repository | Built-in | Repository of the issue |
| Size | Single select | 1, 2, 3, 5 (effort guide, not velocity) |
| Assignees | Built-in | Owner(s) of the story |

## Views

| View | Layout | Configuration |
| --- | --- | --- |
| Board | Board | Group by Status, filter `sprint:S1` (current sprint) |
| Sprints | Table | Group by Sprint |
| Per person | Table | Group by Assignees |
| Needs review | Table | Filter `status:"In review"`, sort by updated |
| My items | Table | Filter `assignee:@me -status:Done` |

## Workflows (built-in automations)

- Item added to the Project → Status **Backlog**
- Pull request linked → Status **In review**
- Issue closed or pull request merged → Status **Done**
- Auto-add: new issues from the five repositories

## Labels (same set in every repository)

`epic`, `story`, `task`, `bug`, `blocked`, `ai-assisted`, `sprint-1` … `sprint-5`
(created by `.github/scripts/setup-org.sh`)
