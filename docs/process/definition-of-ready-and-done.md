# Definition of Ready and Definition of Done

## Definition of Ready

A story can enter a sprint when:

- [ ] It follows the story format: *As a …, I want …, so that …*
- [ ] It has testable acceptance criteria.
- [ ] It is small enough to finish within the sprint. A story that needs more than a few working
      days is split.
- [ ] It has a proposed owner.
- [ ] Its dependencies are known and linked.
- [ ] If it touches an endpoint, the OpenAPI contract is agreed.
- [ ] It lives in the repository whose code it changes. A cross-repository story has one parent
      issue and one child issue per repository.

## Definition of Done

A story is done when:

- [ ] Tests pass and cover the acceptance criteria.
- [ ] CI is green on the pull request and on `main` after merge.
- [ ] At least one review by a member from another layer.
- [ ] Documentation is updated (README, OpenAPI, ADR when a decision was made).
- [ ] Metrics are updated for backend features (counters or histograms exposed on `/metrics`).
- [ ] It is deployed on the sprint's target environment.
- [ ] The author can explain the change, including any AI-generated part.
- [ ] The issue is closed and the GitHub Project item is in **Done**.

## Sprint target environments

| Sprint | Target environment |
| --- | --- |
| S1 | Docker Compose (local stack from horizon-infrastructure) |
| S2 | Docker Compose with local Prometheus |
| S3 | Docker Compose with worker and WebSocket |
| S4 | kind in CI, then the demo cluster (minikube) |
| S5 | Demo cluster with SLOs, alerts and dashboards |
