# overthinkos/fedora

The **Fedora image-family showcase** for [Overthink](https://github.com/overthinkos/overthink),
split into its own repository and mounted as a git submodule at `image/fedora`
of the main repo.

## What's here

| Kind | Entries |
|---|---|
| `image:` | `fedora-coder` (kitchen-sink dev image), `fedora-ov` (minimal ov toolchain, disabled), `fedora-test` (traefik/testapi integration fixture, disabled) |

The Fedora **base stack** (`fedora`, `fedora-builder`, `fedora-nonfree`) is
**not** here — it stays in the main repo (see "Why the base stays in main"
below).

## Composition by reference — nothing is vendored

This repo contains **no layers, no build-config, and no base of its own**.
Everything is pulled from `github.com/overthinkos/overthink` by **github
reference**:

- every layer in `box.yml` is an `@github.com/overthinkos/overthink/candy/<name>:<tag>` ref;
- the shared build-config (`build.yml` — distro/builder/init, including the
  `fedora` distro definition + the `rpm` format template) is a remote `include:`;
- the Fedora base stack (`fedora` + `fedora-builder` + `fedora-nonfree`) is a
  remote `include:` of the main repo's `fedora-base.yml`.

Layer refs + `build.yml` pin to the ecosystem layer tag; the `fedora-base.yml`
file include pins to the fresh main tag that first carries it (the file does not
exist at the older ecosystem layer tag). There is exactly one definition of
every layer/base — no duplication.

## Why the base stays in main (arch precedent, not debian's)

Fedora is the ecosystem **default base**: ~40 main images root on `fedora` /
`fedora-nonfree` (jupyter, immich, hermes, selkies-desktop, nvidia, the openclaw
family, the eval beds, …) and `fedora-builder` is main's `defaults.builder`. So
the base stack physically belongs in main — it lives in the main repo's
`fedora-base.yml`, included locally by main AND remotely by this repo (the **arch
precedent**; debian/ubuntu moved their bases entirely because nothing in main
consumed them).

## No coupling with main

Nothing in the main `overthink` repo consumes any image **here** (the showcase
images have no in-main dependents), so there is **no main → fedora coupling**:
main owns `fedora-base.yml` locally and remote-includes nothing from this repo.
The only edge is `fedora → main` (this repo pulls layers + `build.yml` +
`fedora-base.yml`). The image DAG is acyclic
(`fedora-coder → fedora-nonfree → fedora → quay.io/fedora/fedora:43`).

## Build

```bash
# Inside the submodule (the build verb defaults to overthink.yml):
ov box build fedora-coder

# From the parent overthink repo:
ov -C image/fedora image build fedora-coder

# Standalone, against the published repo:
ov --repo overthinkos/fedora image build fedora-coder
```

The first build resolves the upstream github references into
`~/.cache/ov/repos/` and materializes the referenced layers under
`.build/_layers/`.

## Requirements

A build of any image here fetches from the upstream repo, so it needs network
access and an `ov` recent enough to understand the config's schema version
(`ov` hard-fails with an "update ov" message if the config is newer than the
binary supports).

---
*Assisted-by: Claude*
