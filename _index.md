---
emoji: 🤹🏻‍♀️
title: Learning github actions
description: My notes on understanding Github actions.
date: 2022-01-31 22:15:00
---

These are my notes from [https://www.actionsbyexample.com/](https://www.actionsbyexample.com/)

Actions are configured by writing "workflows" in `YAML` files under the directory `.github/workflows`. These are executed in order of their name

Typical example is,

```yaml
on:
  push:
    branches:
      - 'main'
jobs:
  build: # Name of the jobs
    runs-on: macos-latest
    env:
      VERSION_NUMBER: 'v0.0.0' # Environment Variable at the job-level
    steps:
      - name: Checking out code # Github action name
        uses: actions/checkout@v3 # Github action to be used
        with:
          fetch-depth: 0 # variables to be used with the above package
```

## Examples:

- [https://github.com/lilyhill/devkit/blob/main/.github/workflows/workflows.yaml](https://github.com/lilyhill/devkit/blob/main/.github/workflows/workflows.yaml)

## Questions:

- How to have incremental build numbers, after merging master?
  - Stuff tried:
    - `damienaicheh/extract-version-from-tag-action@v1.0.0` unable to increment. Even though it gets te tag action properly

## Packages I use:

- `subosito/flutter-action@v2` 
  - Use macos flutter to build flutter mac apps
- `marvinpinto/action-automatic-releases@latest`
  - Create a Release page
  - unable to figure out how to make incremental release page

