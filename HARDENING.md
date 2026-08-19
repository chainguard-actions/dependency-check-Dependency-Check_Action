<!-- markdownlint-disable -->

# Hardening Report: dependency-check--Dependency-Check_Action/1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dependency-check--Dependency-Check_Action/1.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 2 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The Docker action's runs.image field references 'docker://owasp/dependency-check-action:latest', which uses a mutable ':latest' tag instead of an immutable SHA digest (e.g. @sha256:<64-hex-char-digest>). A supply-chain attacker who pushes a malicious image to that tag would have it automatically executed by any workflow using this action.

Locations:

- `action.yml:18`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the mutable 'docker://owasp/dependency-check-action:latest' image reference in action.yml to the immutable digest 'docker://owasp/dependency-check-action:latest@sha256:fa1634e8b3114757684835ee27cc6db161dde7b2d6d3047079ff943dabe57ce2'. The docker:// scheme and :latest tag are preserved inline as required.

### Iteration 2

**Fixes applied:** unpinned-uses

**Notes:**

The finding claimed the SHA256 digest was 63 hex characters (truncated). After careful character-by-character counting, the digest `fa1634e8b3114757684835ee27cc6db161dde7b2d6d3047079ff943dabe57ce2` is exactly 64 hex characters. The Docker registry API confirmed this same digest for `owasp/dependency-check-action:latest`. The image reference in action.yml already correctly uses the `docker://` scheme, keeps the `:latest` tag inline, and appends the SHA256 digest — making it properly pinned. No changes were required as the file already contained the correct registry-verified digest.

