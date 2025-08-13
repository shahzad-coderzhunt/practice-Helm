## Exercise 01 — Helm Basics

[Notes](./NOTES.md) · [All Exercises](../../README.md#exercises)

I’ll set up my first Helm chart and practice the core commands: `install`, `upgrade`, `rollback`, and `uninstall`.

### Objectives
- Create a starter chart with `helm create`
- Render templates locally
- Install, upgrade (with values), rollback, and uninstall a release

### Steps
```bash
# 1) Create a starter chart
helm create charts/hello-app

# 2) Render the chart locally (dry run)
helm template demo charts/hello-app

# 3) Install using a values file for dev
helm install hello charts/hello-app -n demo --create-namespace \
  -f exercises/01-basics/values-dev.yaml

# 4) Upgrade by changing values (e.g., image.tag or replicaCount)
helm upgrade hello charts/hello-app -n demo \
  -f exercises/01-basics/values-dev.yaml

# 5) View release history and details
helm history hello -n demo
helm get all hello -n demo | cat

# 6) Roll back to a previous revision (if needed)
helm rollback hello 1 -n demo

# 7) Uninstall when done
helm uninstall hello -n demo
```

### Notes
- I’m using `exercises/01-basics/values-dev.yaml` to override defaults. I’ll tweak values as I learn.
- If I’m using Minikube, I make sure Docker context and `kubectl` are pointed to the right cluster.


