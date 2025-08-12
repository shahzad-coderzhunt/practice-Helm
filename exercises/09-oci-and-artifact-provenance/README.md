## Exercise 09 — OCI and Artifact Provenance

I’ll package my chart, push it to an OCI registry, and pull it for install.

### Objectives
- Package charts with `helm package`
- Push/pull using OCI (`helm push`, `helm pull`)
- Optionally sign and verify provenance

### Commands
```bash
# Package the chart
mkdir -p dist
helm lint charts/hello-app
helm package charts/hello-app -d dist

# Login to registry (example: GHCR)
helm registry login ghcr.io -u <USERNAME> --password-stdin

# Push
helm push dist/hello-app-*.tgz oci://ghcr.io/<OWNER>/charts

# Pull and install
helm pull oci://ghcr.io/<OWNER>/charts/hello-app --version <VERSION> -d dist
helm install hello dist/hello-app-<VERSION>.tgz -n demo --create-namespace
```


