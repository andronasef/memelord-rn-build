# memelord-rn-build — Build Agent Instructions

Dedicated build runner repository for building and releasing Android App Bundles (AAB) to Google Play for `andronasef/memelord-rn`.

## Release and Git Tagging

- **Android Releases**: The Android release action (`.github/workflows/android-release.yml`, named `Android Release`) triggers **only on Android-specific git tags** matching the pattern `v*-android` (e.g. `v1.2.3-android`, `v2.1.2-android`).
- **iOS Releases**: Non-Android tags (standard version tags like `v1.2.3` or tags without the `-android` suffix) are reserved for iOS releases and do not trigger the Android release pipeline.
- When creating an Android release:
  1. Ensure version is bumped in `app.json / package.json`.
  2. Create an annotated tag with the `-android` suffix: `git tag -a v<version>-android -m "Release v<version>-android"`.
  3. Push the tag to remote: `git push origin v<version>-android`.
