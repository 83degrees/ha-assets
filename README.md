# ha-assets

Shared public static assets for the Home Assistant estate.

This repository contains only artefacts that are deliberately intended to be
publicly accessible over unauthenticated HTTPS. It is shared infrastructure and
is not owned by any individual product such as MediaCat, ASTV, or AdvMedia.

## Organisation

Content is organised by **artefact purpose/type**, not by consuming product.

For media-entertainment assets, use this convention:

```text
media-assets/
  <domain>/
    images/
    banners/
    theme-music/
```

Initial domains:

```text
media-assets/
  radio/
    images/
    banners/
    theme-music/
  tv/
    images/
    banners/
    theme-music/
```

Examples:

```text
media-assets/radio/images/classic-fm.png
media-assets/tv/banners/bbc-iplayer-wide.png
media-assets/tv/theme-music/bbc-news.mp3
```

Additional domains or asset-type folders should only be introduced when there is
a real requirement.

## Public-content rule

Everything committed to this repository must be safe to expose publicly.

Do not commit:

- Home Assistant configuration;
- secrets, tokens, keys, credentials, or private URLs;
- private product source code or governance material;
- personal or sensitive information.

## Intended delivery

The repository supports two delivery paths:

1. public HTTPS delivery through GitHub Pages for consumers such as Google Cast; and
2. read-only replication of the same assets onto local Home Assistant instances
   for local serving.

The GitHub Pages base URL is:

```text
https://83degrees.github.io/ha-assets/
```

A file such as:

```text
media-assets/radio/images/classic-fm.png
```

is therefore published at:

```text
https://83degrees.github.io/ha-assets/media-assets/radio/images/classic-fm.png
```

The local Home Assistant replication mechanism is still being designed.
