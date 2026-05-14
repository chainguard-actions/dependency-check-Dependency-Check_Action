# Hardening Report: dependency-check--Dependency-Check_Action/1.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **dependency-check--Dependency-Check_Action/1.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The Docker action image reference uses a mutable ':latest' tag instead of an immutable SHA digest. This means the action could silently pull a different (potentially malicious or broken) image on each run. The reference 'docker://owasp/dependency-check-action:latest' should be replaced with a pinned digest such as 'docker://owasp/dependency-check-action@sha256:<64-hex-char-digest>'.

Locations:

- `action.yml:19`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable 'docker://owasp/dependency-check-action:latest' image reference on line 19 of action.yml with the pinned digest 'docker://owasp/dependency-check-action@sha256:8bed1ee2bae627ec4866ca0e423233592e8645ec63413f86326954b738497a38' # latest. The comment outside the YAML quotes preserves the original tag for readability.

