# image/fedora — signpost (not the rule-set)

This submodule owns the **Fedora** showcase images. The fedora base stack lives
in main's `base.yml`; this `charly.yml` imports main under the `charly`
namespace and `build.yml` flat, and adds the fedora-charly / fedora-test images.

**Load these skills FIRST (R0):**

- `/charly-distros:fedora` — the Fedora 43 base image; root of the RPM hierarchy.
- `/charly-distros:fedora-builder`, `/charly-distros:fedora-nonfree`,
  `/charly-distros:rpmfusion` — builder + nonfree repos.
- `/charly-distros:fedora-charly`, `/charly-distros:fedora-test` — the showcase images.
- `/charly-coder:fedora-coder` — the dev image.

**Authoritative rules live in the `opencharly` superproject's root `CLAUDE.md`**
(R0–R10, hard-cutover, AI attribution, git-workflow). This file only signposts
and restates no rule. The multi-agent workflow is in `/charly-internals:agents`.
History lives in `CHANGELOG.md`.
