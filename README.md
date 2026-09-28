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

Local Home Assistant replication is implemented by `83degrees/ha-assets-sync`. The replicated tree is served from `/config/www/ha-assets/` and is therefore available to Home Assistant consumers under `/local/ha-assets/`.


## Adding or replacing shared assets

Use the following operating procedure for assets that are intended to be shared
between Home Assistant/local consumers and public consumers such as Google Cast.

1. Place the asset under the existing purpose/type structure. For media assets,
   prefer `media-assets/<domain>/<asset-type>/...`. Do not introduce a new
   domain or asset-type folder without a real requirement.
2. Use a stable, descriptive filename. Paths and filenames are case-sensitive
   once published and should be treated as consumer-facing identifiers.
3. Confirm the file is safe for unauthenticated public access. Never commit
   secrets, private URLs, personal data, Home Assistant configuration, or
   private product/governance material.
4. Commit the change to `main`. GitHub Pages publishes the corresponding public
   route under:
   `https://83degrees.github.io/ha-assets/<relative-path>`.
5. Allow `ha-assets-sync` on each Home Assistant instance to refresh its local
   mirror. The corresponding local route is:
   `/local/ha-assets/<relative-path>`.
6. When adding a new consumer reference, store the relative asset path in the
   owning product where supported. For MediaCat schema v4, `source_type:
   ha-assets` resolves that one relative path into both the local and external
   routes.
7. For a replacement at the same path, keep the filename unchanged when the
   asset identity has not changed. After the source commit propagates,
   `ha-assets-sync` replaces the local derived copy on its next successful
   sync. Consumers continue using the same route.
8. For a genuine rename or relocation, update all consumer references as a
   coordinated change. Removing or moving a published path without updating
   consumers will break both the public and local routes.

### Verification

For a newly added or replaced asset, verify both delivery paths when relevant:

- public: `https://83degrees.github.io/ha-assets/<relative-path>`;
- Home Assistant local: `/local/ha-assets/<relative-path>`.

For Google Cast artwork, the public HTTPS route is the required consumer route.
For Home Assistant Media Browser and other local consumers, the local
`/local/ha-assets/` route is preferred where the consumer contract specifies
it.

The local mirror is derived and disposable. The authoritative asset remains the
file committed to this repository; do not edit the replicated
`/config/www/ha-assets/` copy directly.
