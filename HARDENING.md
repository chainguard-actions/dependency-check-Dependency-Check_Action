<!-- markdownlint-disable -->

# Hardening Report: dependency-check--Dependency-Check_Action/1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **dependency-check--Dependency-Check_Action/1.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The Docker action references the image 'docker://owasp/dependency-check-action:latest' using a mutable ':latest' tag instead of an immutable SHA digest (e.g., 'docker://owasp/dependency-check-action@sha256:<64-hex-char-digest>'). This means the image pulled at runtime can change without notice, creating a supply-chain attack vector.

Locations:

- `action.yml:16`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable 'docker://owasp/dependency-check-action:latest' image reference in action.yml (line 16) with the immutable digest-pinned form 'docker://owasp/dependency-check-action@sha256:2abeca7cc12bc2d2614adce039f0e806558dc7e62d9665be4f6623c9868b89c7' # latest. The original tag is preserved as a comment for readability.

