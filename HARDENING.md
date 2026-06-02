# Hardening Report: dependency-check--Dependency-Check_Action/1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **dependency-check--Dependency-Check_Action/1.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action uses a Docker image referenced by a mutable tag (`docker://owasp/dependency-check-action:latest`) instead of an immutable SHA digest. This means the image pulled at runtime can change without notice, enabling supply-chain attacks where a compromised or updated image executes arbitrary code in the runner. The `image:` field should be pinned to a specific SHA digest, e.g. `image: owasp/dependency-check-action@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:16`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the mutable Docker image tag `owasp/dependency-check-action:latest` to its immutable SHA256 digest `sha256:78b909a529ed7b1b65e4abef423455acf8cd7ce076e34424328bed241f2b1fb0` in action.yml line 16. The original tag is preserved as a comment (`# latest`) for readability.

