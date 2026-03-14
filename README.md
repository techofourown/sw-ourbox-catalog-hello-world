# sw-ourbox-catalog-hello-world

`sw-ourbox-catalog-hello-world` is a small OurBox application catalog repo.

It consumes the published `hello-world` image from
`sw-ourbox-apps-hello-world` plus the `woodbox-chat` image from
`sw-ourbox-apps-chat`, then publishes a catalog bundle artifact that can be
selected by the installer and expanded into a concrete application set.

## What this repo owns

- the hello-world application catalog definition
- the default app selection for that catalog
- the exact pinned OCI image digest consumed by that catalog
- CI that renders and publishes the catalog bundle

## Consumed application images

- `ghcr.io/techofourown/sw-ourbox-apps-hello-world/hello-world@sha256:d29428789d671b9405ab202413f5eff4d2fb4870f80791050430bce24ccac2d6`
- `ghcr.io/techofourown/sw-ourbox-apps-chat/woodbox-chat@sha256:535b7d4f380a3cfde35501f0303bf4fd26f3bf528670bf05c00c96d0c525c5d2`

## Repository layout

- [catalog/catalog.json](/techofourown/sw-ourbox-catalog-hello-world/catalog/catalog.json)
  - application catalog definition and default app ids
- [catalog/images.lock.json](/techofourown/sw-ourbox-catalog-hello-world/catalog/images.lock.json)
  - exact pinned image refs consumed by this catalog
- [catalog/profile.env](/techofourown/sw-ourbox-catalog-hello-world/catalog/profile.env)
  - small metadata surface that travels with the rendered bundle
- [scripts/render-catalog-bundle.sh](/techofourown/sw-ourbox-catalog-hello-world/scripts/render-catalog-bundle.sh)
  - renders the distributable bundle
- [.github/workflows/publish-catalog-bundle.yml](/techofourown/sw-ourbox-catalog-hello-world/.github/workflows/publish-catalog-bundle.yml)
  - publishes the bundle to GHCR
