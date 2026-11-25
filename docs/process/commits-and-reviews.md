# Commits, branches and reviews

The professor reviews the commit history of every repository: authors, frequency, size and
content. These rules apply to all Horizon repositories and are enforced by the `protect-main`
ruleset, the shared workflows and the templates inherited from the `.github` repository.

## Branches

- `main` is protected: no direct pushes, no force-push, pull request required.
- One issue per branch, named `<type>/<issue>-<short-name>`, for example
  `feature/12-logout-endpoint` or `fix/31-refresh-expiry`.
- Branches are short-lived: merged within about two days, deleted automatically after merge.

## Commits

[Conventional Commits](https://www.conventionalcommits.org/) with the issue number:

```text
<type>(<scope>): <summary in the imperative> (#<issue>)

feat(auth): add logout endpoint (#12)
fix(feed): keep the since cursor after reconnect (#41)
docs(charter): add communication channels (#3)
```

| Type | Use |
| --- | --- |
| `feat` | A new feature for the user |
| `fix` | A bug fix |
| `test` | Tests only |
| `refactor` | Code change with no behaviour change |
| `docs` | Documentation only |
| `ci` | Workflow changes |
| `build` | Dockerfile, dependencies, packaging |
| `chore` | Anything else (tooling, config) |
| `perf` | Performance improvement |

The scope names the module or screen: `auth`, `users`, `connections`, `posts`, `feed`,
`interactions`, `sign-in`, `profile`, `helm`, `compose`, `slo`, …

Enforced locally by a pre-commit hook (backend) or Husky and commitlint (web), and again in CI
(S1-05).

## Pull requests

- Under about 300 changed lines. Split larger work.
- Use the pull request template: linked issue (`Closes #12`), what changed, how it was tested,
  AI note.
- At least one approval from a CODEOWNER, and green CI: the required checks where the repository
  has them (backend today: `test` and `container`; web and infrastructure once the reusable
  workflows of S1-02 land).
- The ruleset enforces the code-owner approval. The cross-layer review (a reviewer from another
  layer, see the Definition of Done) is a team rule, checked in the weekly contributor report.
- Merge method: **rebase and merge** (the only one enabled). Squash would hide the commit
  frequency that is graded.

## Reviews

- Target turnaround: 24 hours. The scrum master lists stale pull requests every Monday.
- Nobody is the only reviewer of their own layer.
- Review for correctness, tests, readability and whether the author can explain it. Use
  suggestions for small fixes.

## Authorship

- Everyone commits under their own account, with their own Git identity.
- Pairing: the person at the keyboard commits, the partner is credited:

  ```text
  feat(users): add search by prefix (#22)

  Co-authored-by: Name <id+login@users.noreply.github.com>
  ```

- Every member commits to at least two repositories; every repository shows at least two authors.
  The weekly contributor report (horizon-infrastructure) checks both.
