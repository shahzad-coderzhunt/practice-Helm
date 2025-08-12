## Exercise 06 — Hooks and Lifecycle

I’ll add lifecycle hooks to run setup tasks during install or upgrade.

### Objectives
- Use pre/post install/upgrade hooks
- Control ordering with `helm.sh/hook-weight` and cleanup with `helm.sh/hook-delete-policy`

### Tasks
- Add a pre-install `Job` that prints a message or performs a readiness check

### Example Hook (Job)
```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: {{ include "hello-app.fullname" . }}-preinstall
  annotations:
    "helm.sh/hook": pre-install
    "helm.sh/hook-weight": "-1"
    "helm.sh/hook-delete-policy": before-hook-creation,hook-succeeded
spec:
  template:
    spec:
      restartPolicy: Never
      containers:
        - name: preinstall
          image: alpine:3.19
          command: ["/bin/sh", "-c", "echo pre-install hook running"]
```


