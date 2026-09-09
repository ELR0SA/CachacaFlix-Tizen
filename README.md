# CachaçaFlix Tizen

A personalized build of the Jellyfin client for Samsung Tizen TVs, patched to play video through Samsung's native **AVPlay** API instead of the standard HTML5 player — this fixes playback hanging forever on certain video files on newer Tizen firmware. This version exists purely as a personal customization, made in homage to my cat.

## Credit

This build stands on the work of others:

- **[jellyfin/jellyfin-tizen](https://github.com/jellyfin/jellyfin-tizen)** — the official Jellyfin client for Samsung TVs
- The AVPlay fix was originally diagnosed and prototyped in [jellyfin-tizen#424](https://github.com/jellyfin/jellyfin-tizen/issues/424)
- **[asamahy/tizen-jellyfin-avplay](https://github.com/asamahy/tizen-jellyfin-avplay)** (10.10.z / SmartHub variant) — the automated build pipeline this fork is based on, itself building on **[PatrickSt1991/tizen-jellyfin-avplay](https://github.com/PatrickSt1991/tizen-jellyfin-avplay)**

## What's different from the automated build this is based on

- App icon replaced with a custom one
- Nothing else — video patch, build target (10.10.z / SmartHub), and install method are unchanged from upstream

## How it builds

`.github/workflows/build-avplay.yml` clones `jellyfin-web` + `jellyfin-tizen`, applies the AVPlay patch and the custom icon, then packages and signs a `.wgt`. `check-upstream.yml` checks for new `jellyfin-web` commits every 12 hours and re-triggers the build automatically, so releases here track upstream Jellyfin closely.

## Install

1. Enable Developer Mode on your Samsung TV
2. Grab the latest `.wgt` from [Releases](../../releases/latest)
3. Sideload it with [Apps2Samsung](https://github.com/Apps2Samsung/Apps2Samsung), Tizen Studio, or `sdb`

### Freeing up space on older TVs

If your TV is low on storage from Samsung's bloatware even though you're not using much of it:

```
Under the Samsung logo on the TV, there's a small black button about 2-3cm in from the bottom edge.
With the TV on:
1. Press and hold that button for 5-10 seconds.
2. Release it.
3. Press and hold the power button on the remote for 5-10 seconds.
4. The TV goes black and restarts — this is the flash reset.
```
