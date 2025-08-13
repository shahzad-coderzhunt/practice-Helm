## Exercise 11 — CI/CD for Charts

[Notes](./NOTES.md) · [All Exercises](../../README.md#exercises)

I’ll automate linting and templating in CI. Optionally I’ll publish packaged charts.

### Objectives
- Run `helm lint` and `helm template` in GitHub Actions
- Optionally add chart packaging and release steps

### Tasks
- Create `.github/workflows/charts-ci.yml` (see sample in repo README)
- Add steps for linting and templating all charts under `charts/`

### Optional
- Integrate `chart-testing` for PR validation
- Push packaged charts to an OCI registry from a `main` branch build


