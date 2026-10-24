# ARCHIVE.md — about this repo

**Permanent archive** of https://github.com/StXaviersOfficial/mojo-swipe-fix — created **2026-10-24** so the swipe-fix source is never lost, even if the original repo is ever deleted.

This is a full git mirror: every branch, every commit, full history of the original.

## Branches

| Branch | What it is |
|---|---|
| `main` | **The swipe fix (v1)** — MojoLauncher source (base: upstream commit `a969175ba`, post-"Iris") with `ControlButton.onTouchEvent` patched: non-swipeable buttons forward MOVE/UP-family events to `ControlLayout`, enabling swiping from a normal key onto a swipeable key (PojavLauncher-style). Last successfully built by GitHub Actions **Jul 17, 2026** (run #39, `:app_pojavlauncher:assembleFullDebug`). |
| `master` | The **v2 always-forward** variant of the fix + 39 commits of CI/NDK build experiments (local `dnbglfw` build). Last successful CI build **Jun 9, 2026**. |

## The fix itself (for the record)

`app_pojavlauncher/src/main/java/net/kdt/pojavlaunch/customcontrols/buttons/ControlButton.java`:
on a non-swipeable button, `ACTION_MOVE` and the `ACTION_UP`-family are additionally
forwarded to `getControlLayoutParent().onTouch(this, event)` so `ControlLayout`'s
`mapTable` can press/release swipeable buttons during the gesture.

## Related artifacts

- Fixed latest APK (official "Justicia" release + v1 fix, smali-level patch, signed):
  https://github.com/StXaviersOfficial/mojo-swipe-fix/releases/tag/justicia-swipefix
- This repo's Releases hold redundant copies of APKs for safekeeping.
