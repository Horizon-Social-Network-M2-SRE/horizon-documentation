# Questions for the professor (week 1, S1-11)

Status: **answered on 2026-11-21**. Answers and their impact are recorded in the
[decisions log](decisions-log.md#answers-from-the-professor).

1. **Repositories.** We use one repository per deployable (horizon-backend, horizon-web) plus
   horizon-infrastructure and horizon-documentation. Does this match "1 repo per service"?
2. **Modular backend.** The backend is one FastAPI service split into modules (auth, users,
   connections, posts, feed, interactions), plus a Celery worker deployed separately from the same
   image. Is a modular monolith accepted, or do you expect several backend services?
3. **Mobile app.** We plan mobile-first layouts and an optional installable PWA instead of a native
   app. Does a PWA count as the mobile application?
4. **Istio equivalent.** We plan Prometheus, Grafana, Traefik ingress metrics and blackbox probes,
   without a service mesh. Is that an acceptable equivalent to Istio?
5. **Demo environment.** The demo cluster is an EKS cluster emulated locally by Floci (k3s
   underneath), running on a team laptop. Is an emulated EKS cluster accepted, and is a live demo
   from a laptop (or a recorded run as a fallback) fine for the milestone presentations?
6. **Repository visibility.** Our repositories are public so that branch protection works on the
   GitHub Free plan. Is that acceptable, or should they be private?
