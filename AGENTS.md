# memelord-rn-build — Build Agent Instructions

Dedicated build runner repository for building and releasing Android App Bundles (AAB) to Google Play for `andronasef/memelord-rn`.

## Release and Git Tagging

- Triggered via `workflow_dispatch` with an input `ref` passed from the source repository `andronasef/memelord-rn`.
- Tags are formatted as `v*-android` (e.g. `v1.2.3-android`).
- Workflow file: `.github/workflows/android-release.yml` (named `Android Release`).
