# memelord-rn-build

Free-minutes CI mirror for the **private** app repo
[`andronasef/memelord-rn`](https://github.com/andronasef/memelord-rn).

GitHub bills Actions minutes for private repos but gives **public** repos
unlimited free standard runners. This public repo holds only the workflow YAML —
no app source. Each workflow checks out the private source via a PAT and runs the
identical Android build, so builds cost **0 included minutes**.

## Builds

Trigger from the **Actions** tab → pick a workflow → **Run workflow**:

- **Android Debug Build** — builds a debug APK, attaches it to a GitHub
  pre-release for easy install.
- **Android Release (Google Play draft)** — builds the signed AAB and uploads it
  to Google Play as a **draft** (production track). Publish manually from the
  Play Console. No binaries are attached to GitHub.

## Required secrets

Set under **Settings → Secrets and variables → Actions**:

| Secret | Used by | Notes |
| --- | --- | --- |
| `SOURCE_REPO_TOKEN` | both | Fine-grained PAT on `memelord-rn`, **Contents: read** — checks out the private source. |
| `GOOGLE_SERVICES_JSON_BASE64` | both | base64 of `google-services.json`. |
| `ANDROID_KEYSTORE_BASE64` | release | base64 of the release `key.jks`. |
| `ANDROID_STORE_PASSWORD` | release | keystore store password. |
| `ANDROID_KEY_ALIAS` | release | signing key alias. |
| `ANDROID_KEY_PASSWORD` | release | signing key password. |
| `PLAY_SERVICE_ACCOUNT_JSON` | release | Google Play service account JSON. |

All except `SOURCE_REPO_TOKEN` mirror the secrets already on `memelord-rn`.
