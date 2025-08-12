## Exercise 02 — Templating Fundamentals

I’ll practice Go templating features and make my chart configurable via values.

### Objectives
- Use `if`, `range`, `default`, `required`, and `include`
- Convert maps/arrays to YAML using `toYaml` and `nindent`
- Try `tpl` for rendering templates from values

### Tasks
- Parameterize `Service` type, `Deployment` replicas, labels, and annotations using values
- Add optional pod annotations and environment variables via values
- Use `tpl` to render a small annotation block defined in values

### Commands
```bash
# Render with custom values to see changes
helm template demo charts/hello-app -f exercises/01-basics/values-dev.yaml | cat

# Optionally add more overrides inline
helm template demo charts/hello-app \
  --set service.type=LoadBalancer \
  --set replicaCount=3 | cat
```


