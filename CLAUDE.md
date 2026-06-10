# image/fedora — signpost (not the rule-set)

This submodule is **self-contained**: it OWNS the full Fedora base/builder stack
locally (`fedora` → `fedora-nonfree` → `fedora-builder`), the Fedora **GPU base
family** (`nvidia` / `python-ml`), the consumer showcase images (`fedora-coder` /
`charly-fedora` / `fedora-test`), the `sway-browser-vnc` desktop, and the ~29
relocated Fedora-rooted app/fixture boxes (jupyter, jupyter-ml, comfyui, ollama,
unsloth-studio, immich, immich-ml, openwebui, hermes, web, eval-pod, redis,
tier1/tier23, …) — all discovered under `box/`. It vendors **no candies**: every
candy is an `@github.com/overthinkos/overthink/candy/<name>:<tag>` ref into main's
shared candy library, so there is no `candy/` dir here. Every box's base is a bare
LOCAL name (`base: fedora` / `fedora-nonfree` / `nvidia`); the distro/builder/init
build vocabulary is embedded in the `charly` binary. There is NO namespace import
(`import: []`). Main imports THIS repo under the `fedora` namespace to build the
relocated boxes; this repo imports nothing back (the former two-way main↔fedora
import is dissolved).

**Load these skills FIRST (R0):**

- `/charly-distros:fedora` — the Fedora 43 base image; root of the RPM hierarchy.
- `/charly-distros:fedora-builder`, `/charly-distros:fedora-nonfree`,
  `/charly-distros:rpmfusion` — builder + nonfree repos.
- `/charly-distros:charly-fedora`, `/charly-distros:fedora-test` — the showcase images.
- `/charly-coder:fedora-coder` — the dev image.
- `/charly-distros:nvidia`, `/charly-distros:cuda` — the Fedora GPU base (`nvidia`
  box) + CUDA toolkit; `python-ml` builds on it.
- `/charly-selkies:sway-browser-vnc` — the minimal Sway + wayvnc + Chrome desktop.

**Authoritative rules live in the `opencharly` superproject's root `CLAUDE.md`**
(R0–R10, hard-cutover, AI attribution, git-workflow). This file only signposts
and restates no rule. The multi-agent workflow is in `/charly-internals:agents`.
History lives in `CHANGELOG.md`.
