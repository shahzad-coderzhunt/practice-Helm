## Exercise 10 — Environments and Helmfile

I’ll manage multiple releases and environments declaratively with Helmfile.

### Objectives
- Define environments and releases in `helmfile.yaml`
- Diff and apply changes per environment

### Files in this folder
- `helmfile.yaml`: starter file referencing my chart and values

### Commands
```bash
# Install helmfile (one option)
brew install helmfile || choco install helmfile || scoop install helmfile

# Show planned changes
helmfile -e dev -f exercises/10-environments-and-helmfile/helmfile.yaml diff

# Apply dev and staging
helmfile -e dev -f exercises/10-environments-and-helmfile/helmfile.yaml apply
helmfile -e staging -f exercises/10-environments-and-helmfile/helmfile.yaml apply
```

### Note
- Update chart and values paths in `helmfile.yaml` if my repo layout differs.


