# Hardening Report: dependency-check--Dependency-Check_Action/1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **dependency-check--Dependency-Check_Action/1.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action uses a Docker image referenced by a mutable tag ('latest') instead of an immutable SHA digest. This means the action could silently pull a different (potentially malicious) image on each run. The failing reference is: image: 'docker://owasp/dependency-check-action:latest'. It should be pinned to a specific SHA digest, e.g. 'docker://owasp/dependency-check-action@sha256:<64-hex-char-digest>'.

Locations:

- `action.yml:14`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from the mutable 'owasp/dependency-check-action:latest' tag to the immutable digest 'owasp/dependency-check-action@sha256:a972e934cbf21a5ebee339dec0b3a99411611a1f27112b41511e1f93a6ced9e7', with '# latest' comment preserved for readability.

