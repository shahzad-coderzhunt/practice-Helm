## Exercise 03 — Helpers and Partials

I’ll DRY up templates using `_helpers.tpl` for names, labels, and shared snippets.

### Objectives
- Create standard labels and names in `_helpers.tpl`
- Reuse helpers across `Deployment`, `Service`, and other manifests

### Tasks
- Add helpers: `mychart.name`, `mychart.fullname`, and `mychart.labels`
- Replace repeated label/name blocks with helper calls
- Keep labels consistent across all resources

### Tip
- I’ll follow Helm’s official label recommendations in the template guide.


