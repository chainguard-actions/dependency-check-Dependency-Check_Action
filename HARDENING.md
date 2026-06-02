# Hardening Report: dependency-check--Dependency-Check_Action/1.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **dependency-check--Dependency-Check_Action/1.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action uses a Docker image referenced by a mutable tag (`latest`) instead of an immutable SHA digest. `image: 'docker://owasp/dependency-check-action:latest'` can silently change to a different (potentially malicious) image at any time. It should be pinned to a specific SHA256 digest, e.g. `image: 'docker://owasp/dependency-check-action@sha256:<64-hex-char-digest>'`.

Locations:

- `action.yml:16`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image reference `docker://owasp/dependency-check-action:latest` with the immutable digest `docker://owasp/dependency-check-action@sha256:78b909a529ed7b1b65e4abef423455acf8cd7ce076e34424328bed241f2b1fb0` in action.yml line 16. The `# latest` comment is preserved outside the YAML quotes for readability.

