# ci

Shared GitHub Actions workflows for beckley113 repos.

## Node / TypeScript

Add `.github/workflows/ci.yml` to a repo:

```yaml
name: CI
on:
  pull_request:
  push:
    branches: [main]
jobs:
  ci:
    uses: beckley113/ci/.github/workflows/node.yml@main
```

The workflow runs `npm ci`, then each of these scripts if the repo defines it:
`typecheck`, `lint`, `format:check`, `test`, `build`.

Optional inputs:

```yaml
    with:
      node-version: "22"   # default: .nvmrc, .node-version, then 22
      build: false          # skip the build step
      build-env: |          # placeholder env vars the build needs (no secrets)
        NEXT_PUBLIC_CONVEX_URL=https://placeholder.convex.cloud
```

Changes to `main` here apply to every repo on its next run.
