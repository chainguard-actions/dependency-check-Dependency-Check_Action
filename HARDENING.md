<!-- markdownlint-disable -->

# Hardening Report: dependency-check--Dependency-Check_Action/1.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dependency-check--Dependency-Check_Action/1.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The Docker action's runs.image uses a mutable tag instead of a SHA digest: `image: 'docker://owasp/dependency-check-action:latest'`. Pin it to a digest, e.g. `docker://owasp/dependency-check-action@sha256:<digest> # latest`.

Locations:

- `action.yml:18`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned runs.image to docker://owasp/dependency-check-action:latest@sha256:0baed58d5d34257d13f04cda00b3928a6f1db238fe6014723d80e5725b2d059d. The docker:// scheme and the tag are still there. Args are unchanged.

