## Exercise 05 — Dependencies and Umbrella Charts

I’ll add chart dependencies and practice the umbrella pattern.

### Objectives
- Declare dependencies in `Chart.yaml`
- Enable/disable subcharts via values and pass global values

### Tasks
- In `charts/hello-app/Chart.yaml`, add a dependency (e.g., Bitnami `redis`)
- Run `helm dependency update` and install the umbrella

### Example Snippet (Chart.yaml)
```yaml
dependencies:
  - name: redis
    version: "~19.0.0"
    repository: "https://charts.bitnami.com/bitnami"
    condition: redis.enabled
```

### Commands
```bash
helm dependency update charts/hello-app
helm install hello charts/hello-app -n demo --create-namespace
```


