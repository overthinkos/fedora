# image/fedora — signpost (not the rule-set)

This submodule owns the **Fedora** showcase images. The fedora base stack lives
in main's `base.yml`; this `overthink.yml` imports main under the `ov`
namespace and `build.yml` flat, and adds the fedora-ov / fedora-test images.

**Load these skills FIRST (R0):**

- `/ov-distros:fedora` — the Fedora 43 base image; root of the RPM hierarchy.
- `/ov-distros:fedora-builder`, `/ov-distros:fedora-nonfree`,
  `/ov-distros:rpmfusion` — builder + nonfree repos.
- `/ov-distros:fedora-ov`, `/ov-distros:fedora-test` — the showcase images.
- `/ov-coder:fedora-coder` — the dev image.

**Authoritative rules live in the `overthink` superproject's root `CLAUDE.md`**
(R0–R10, hard-cutover, AI attribution, git-workflow). This file only signposts
and restates no rule. The multi-agent workflow is in `/ov-internals:agents`.
History lives in `CHANGELOG.md`.
