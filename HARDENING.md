# Hardening Report: dependency-check--Dependency-Check_Action/1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **dependency-check--Dependency-Check_Action/1.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The Docker action references a mutable image tag instead of a SHA digest. `image: 'docker://owasp/dependency-check-action:latest'` uses the `:latest` tag, which can change at any time and is vulnerable to supply-chain attacks. It should be pinned to a specific SHA digest, e.g. `image: 'docker://owasp/dependency-check-action@sha256:<64-hex-char-digest>'`.

Locations:

- `action.yml:16`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable `docker://owasp/dependency-check-action:latest` image reference in action.yml (line 16) with the pinned digest `docker://owasp/dependency-check-action@sha256:78b909a529ed7b1b65e4abef423455acf8cd7ce076e34424328bed241f2b1fb0 # latest`. The SHA digest was resolved via the Docker Registry API.

