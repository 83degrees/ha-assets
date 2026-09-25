# ha-assets

Shared public static assets for the Home Assistant estate.

This repository contains only artefacts that are deliberately intended to be
publicly accessible over unauthenticated HTTPS. It is shared infrastructure and
is not owned by any individual product such as MediaCat, ASTV, or AdvMedia.

## Organisation

Content is organised by **artefact type**, not by consuming product.

Initial structure:

```text
images/
  radio/
  tv/
```

Additional top-level artefact types should only be introduced when there is a
real requirement.

## Public-content rule

Everything committed to this repository must be safe to expose publicly.

Do not commit:

- Home Assistant configuration;
- secrets, tokens, keys, credentials, or private URLs;
- private product source code or governance material;
- personal or sensitive information.

## Intended delivery

The repository is intended to support two delivery paths:

1. public HTTPS delivery for consumers such as Google Cast, using GitHub Pages
   or another agreed public delivery layer; and
2. read-only replication of the same assets onto local Home Assistant instances
   for local serving.

The public delivery mechanism and local replication mechanism are still being
designed.
