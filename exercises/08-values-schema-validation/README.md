## Exercise 08 — Values Schema Validation

I’ll enforce input validation using `values.schema.json`.

### Objectives
- Define types, required fields, and enums for values
- Validate early via `helm lint` and `helm template`

### Tasks
- Copy the provided `values.schema.json` from this folder into `charts/hello-app/`
- Adjust the schema as my chart evolves

### Commands
```bash
cp exercises/08-values-schema-validation/values.schema.json charts/hello-app/values.schema.json
helm lint charts/hello-app
helm template demo charts/hello-app -f exercises/01-basics/values-dev.yaml | cat
```


