# release-action

automated releases based on conventional commits

## Usage

1. add a `RELEASE_TOKEN` actions secret with:
- Repo access to workflow repo
- Commit statuses `ro`
- Contents `rw`
- Pull requests `rw`

2. Create a new release
- just `v0.1.0` in tag field

3. Add this workflow:
```yaml
name: Release

on:
  push:
    branches:
      - main

permissions:
  contents: write
  pull-requests: write

jobs:
  release-please:
    runs-on: ubuntu-latest
    steps:
      - uses: matt-888/release-action@main
        with:
          token: ${{ secrets.RELEASE_TOKEN }}
          type: python
```
