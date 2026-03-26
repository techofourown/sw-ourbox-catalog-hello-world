# sw-ourbox-catalog-hello-world

`sw-ourbox-catalog-hello-world` is a small OurBox application catalog repo.

It consumes the published `hello-world` image from
`sw-ourbox-apps-hello-world` plus the `ourbox-chat` image from
`sw-ourbox-apps-chat`, then publishes a catalog bundle artifact that can be
selected by the installer and expanded into a concrete application set.

## What this repo owns

- the hello-world application catalog definition
- the default app selection for that catalog
- the source refs that should be resolved into the published image lock
- CI that renders and publishes the catalog bundle

Shared tooling scripts are pulled automatically at CI time via `bootstrap.sh`
from the catalog-tooling OCI artifact. They are not checked into the repo.

## Consumed application images

- `ghcr.io/techofourown/sw-ourbox-apps-hello-world/hello-world:latest`
- `ghcr.io/techofourown/sw-ourbox-apps-chat/ourbox-chat:latest`

This repo also publishes installer-browsable catalog rows at
`ghcr.io/techofourown/sw-ourbox-catalog-hello-world:catalog-amd64`. Those rows
let host-side installers resolve the newest stable pinned bundle for the
requested channel and architecture.

## Repository layout

- [bootstrap.sh](/techofourown/sw-ourbox-catalog-hello-world/bootstrap.sh)
  - pulls shared tooling scripts from the catalog-tooling OCI artifact
- [catalog/catalog.json](/techofourown/sw-ourbox-catalog-hello-world/catalog/catalog.json)
  - application catalog definition and default app ids
- [catalog/image-sources.json](/techofourown/sw-ourbox-catalog-hello-world/catalog/image-sources.json)
  - source refs that are resolved into a generated `dist/images.lock.json` during publish
- [catalog/profile.env](/techofourown/sw-ourbox-catalog-hello-world/catalog/profile.env)
  - small metadata surface that travels with the rendered bundle
- [.github/workflows/publish-catalog-bundle.yml](/techofourown/sw-ourbox-catalog-hello-world/.github/workflows/publish-catalog-bundle.yml)
  - publishes the bundle to GHCR
