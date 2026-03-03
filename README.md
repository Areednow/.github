# Areednow/.github

Shared GitHub configuration for the Areednow organization.

## What's in this repo

| Path | Purpose |
|------|---------|
| `profile/README.md` | Public organization profile shown at github.com/Areednow |
| `.github/workflows/node-ci.yml` | Reusable Node.js CI workflow (build + lint + typecheck) |
| `.github/workflows/deno-lint.yml` | Reusable Deno lint workflow for Supabase Edge Functions |

## Usage

### Node CI

In your repo's `.github/workflows/ci.yml`:

```yaml
name: CI
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  node-ci:
    uses: Areednow/.github/.github/workflows/node-ci.yml@main
    with:
      node-version: "20"
      run-build: true
      run-typecheck: true
```

### Deno Lint (for repos with Supabase Edge Functions)

```yaml
jobs:
  deno-lint:
    uses: Areednow/.github/.github/workflows/deno-lint.yml@main
    with:
      lint-path: "supabase/functions/"
```

## Adding a New Reusable Workflow

1. Create the workflow in `.github/workflows/` with `on: workflow_call`
2. Document inputs and usage in this README
3. Reference it from consumer repos using `uses: Areednow/.github/.github/workflows/<name>.yml@main`
