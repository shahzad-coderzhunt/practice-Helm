## Exercise 12 — Advanced Patterns

[Notes](./NOTES.md) · [All Exercises](../../README.md#exercises)

I’ll extract reusable logic into library charts and use advanced templating.

### Objectives
- Create a library chart for labels, helpers, and common manifests
- Consume the library from my application chart
- Apply upgrade-safe patterns for immutable fields and rollouts

### Tasks
- Create `charts/common-lib` with `type: library`
- Move shared helpers into the library and reference them in `hello-app`
- Use `tpl` for nested templating where appropriate


