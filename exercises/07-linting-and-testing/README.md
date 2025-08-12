## Exercise 07 — Linting and Testing

I’ll validate charts with linting and add unit tests with a plugin.

### Objectives
- Run `helm lint` and fix issues
- Add unit tests with `helm-unittest` or use `chart-testing`

### Commands
```bash
# Lint the chart
helm lint charts/hello-app

# Install helm-unittest plugin
helm plugin install https://github.com/helm-unittest/helm-unittest

# Create a tests directory in the chart and add test files
mkdir -p charts/hello-app/tests

# Example: run tests
helm unittest charts/hello-app
```


