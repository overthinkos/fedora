# image/fedora — signpost (not the rule-set)

This submodule owns the **Fedora** showcase images PLUS the **Fedora GPU base
family** (`nvidia` / `python-ml`) and the `sway-browser-vnc` desktop. The fedora
base stack lives in main's `base.yml`; this `charly.yml` imports main under the
`charly` namespace and `build.yml` flat. Main consumes the GPU base here as
`base: fedora.nvidia` (its comfyui / jupyter-ml / jupyter-ml-notebook / ollama /
unsloth-studio pod families) — a MUTUAL import (main mounts this repo under
`fedora`; this repo imports main under `charly`), cycle-broken at load by the
`repo:` field.

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
