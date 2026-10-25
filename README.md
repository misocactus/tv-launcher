# Living Room

A quiet, tvOS-style launcher for a Samsung The Frame (Tizen), delivered as a
[TizenBrew](https://github.com/reisxd/TizenBrew) app module.

## Why

Samsung's Smart Hub leads with ads and Samsung's own priorities. This replaces it
with the apps actually installed on the TV, one dock, and a "shelf" that shows
what is waiting inside the focused app — real data where we own it, an honest
panel where the app exposes nothing.

## Install on the TV

1. Open **TizenBrew** on the TV.
2. Top bar → box icon (**Module Manager**).
3. **Add GitHub Module**.
4. Enter: `misocactus/tv-launcher`
5. Launch the **Living Room** tile.

## Iterating

The module is served from jsDelivr straight out of this repo:

```
https://cdn.jsdelivr.net/gh/misocactus/tv-launcher/package.json
```

So a `git push` is a deploy — reopen the module and the TV picks it up. jsDelivr
caches branch content for up to ~12 hours; to bust it:

```
curl https://purge.jsdelivr.net/gh/misocactus/tv-launcher@main/app/index.html
```

## Keys

- Arrows: move
- OK / Enter: launch the focused app
- Back: return
- **D**: debug panel — lists every installed app with its real app id and icon
  path. Screenshot it to pin favourites.

## How it behaves

- Reads the installed apps from the TV (`tizen.application.getAppsContext`) and
  renders them; no hardcoded app ids.
- Favourite row = first six matches against a known-apps pattern.
- Sound: four generated clicks (scroll tick, open, back, launch) embedded as
  base64 WAVs — no network fetch, no assets.
- Anything without an icon falls back to a coloured wordmark.

## Status

v0.1.0 — first install. Open questions: icon loading from `iconPath`, latency of
UI clicks through eARC, and whether any of the streaming apps expose data for the
shelf (they do not, so far).

## Licence

MIT for this code. TizenBrew is GPL-3.0 and is a separate project.
