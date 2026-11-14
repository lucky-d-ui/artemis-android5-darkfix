# Artemis Android 5 Dark Theme Fix

**An unofficial compatibility build of [Artemis Android](https://github.com/ClassicOldSong/moonlight-android) for older Android devices.**

This repository preserves the source code of **Artemis v20.0.0+250712** with a minimal theme change that makes the Settings screen readable on an Android 5.1.1 tablet. It is based on Artemis, a fork of [Moonlight Android](https://github.com/moonlight-stream/moonlight-android), and is intended for use with [Apollo](https://github.com/ClassicOldSong/Apollo) or compatible streaming hosts.

> [!IMPORTANT]
> This is an **unofficial, community-modified build**, not a release by the Artemis, Apollo, or Moonlight developers. It is not an upgrade to the latest Artemis version.

## Why this build exists

On a Huawei MediaPad M2 running Android 5.1.1, Artemis v20.0.0 launched and streamed successfully, but the Settings screen displayed dark text on a dark background. Newer Artemis builds tested on that tablet exited unexpectedly.

The only intentional application source change in this version is in [`app/src/main/res/values-v21/styles.xml`](app/src/main/res/values-v21/styles.xml):

```diff
-    <style name="AppBaseTheme" parent="Theme.AppCompat.DayNight.NoActionBar">
+    <style name="AppBaseTheme" parent="Theme.AppCompat.NoActionBar">
```

This forces the AppCompat dark theme for API 21+ in this build instead of automatically selecting a DayNight variant. The goal is **readable settings**, not additional streaming features. The modification was made in November 2026.

## Compatibility

| Device / feature | Result |
| --- | --- |
| Huawei MediaPad M2, Android 5.1.1 | **Tested working** |
| Apollo virtual display, wireless streaming | **Tested working** |
| Touch input and on-screen performance statistics | **Tested working** |
| Other Android 5.x devices | **Not tested** |
| Other Android versions / devices | **Not tested** |

The project's original minimum Android API level is 21 (Android 5.0), but that does **not** guarantee this modified build works on every Android 5.x device.

## Download and install

Download the APK from this repository's **[Releases](../../releases)** page when a release is available.

The tested APK was built using the `nonRoot_gameDebug` variant. It appears as **Diana (Game)** and uses the package ID `com.limelight.noirdebug`, allowing it to be installed alongside the original Artemis release. This is a **debug build signed for testing**, not an official release-signed APK.

1. Install the APK on your Android device.
2. Pair Diana with your Apollo host.
3. In Apollo's **Device Management**, grant the new client the necessary streaming and input permissions (especially **View Streams**, **Launch Apps**, and **Touch Input** as needed).
4. Choose the desired streaming resolution, frame rate, touch mode, and performance overlay in Diana's settings.

Use only builds from sources you trust, and check your host's permissions before granting remote input or command access.

## Source code

This repository contains the modified Artemis v20.0.0+250712 source tree, including the `moonlight-common-c` native sources and their included dependencies. It is kept here so the modified version remains accessible even if the upstream release is no longer available.

This repository does **not** guarantee a completely offline or reproducible build: Android SDK/NDK, Gradle dependencies, and a compatible build environment may still be required. The original project's build instructions are available at [ClassicOldSong/moonlight-android](https://github.com/ClassicOldSong/moonlight-android).

## Credits and license

- **[Artemis Android / Moonlight Noir](https://github.com/ClassicOldSong/moonlight-android)** — upstream project maintained by **ClassicOldSong**.
- **[Moonlight Android](https://github.com/moonlight-stream/moonlight-android)** — original client project. Original README credits Cameron Gutman, Diego Waxemberg, Aaron Neyer, and Andrew Hennessy, as well as other contributors.
- **[Apollo](https://github.com/ClassicOldSong/Apollo)** — companion streaming host by ClassicOldSong.

The original project is distributed under the **GNU General Public License v3.0**; see [`LICENSE.txt`](LICENSE.txt). Existing copyright notices and third-party licenses in the source tree remain applicable. No affiliation with or endorsement by the upstream developers is claimed.
