## Exercise 04 — Values and Overrides

[Notes](./NOTES.md) · [All Exercises](../../README.md#exercises)

I’ll learn how layered values work and how precedence is applied.

### Objectives
- Use `values.yaml` defaults and environment-specific files
- Understand precedence of `-f` files and `--set`

### Tasks
- Create `values/dev.yaml`, `values/staging.yaml`, and `values/prod.yaml` at the repo root under `values/`
- Try different combinations of `-f` files and `--set` flags and inspect the rendered output

### Commands
```bash
# Example: render with dev values
helm template demo charts/hello-app -f values/dev.yaml | cat

# Multiple files: later files override earlier ones
helm template demo charts/hello-app -f values/dev.yaml -f values/local-overrides.yaml | cat

# Inline overrides have highest precedence
helm template demo charts/hello-app -f values/dev.yaml --set replicaCount=3 | cat
```


