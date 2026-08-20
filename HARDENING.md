<!-- markdownlint-disable -->

# Hardening Report: dependency-check--Dependency-Check_Action/1.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dependency-check--Dependency-Check_Action/1.1.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The docker action references a mutable image tag instead of an immutable SHA digest. `image: 'docker://owasp/dependency-check-action:latest'` uses the `:latest` tag, which can be silently replaced with a different (potentially malicious) image at any time, creating a supply-chain attack vector. It should be pinned to a specific SHA digest, e.g. `docker://owasp/dependency-check-action@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:20`

### script-injection (severity: high)

Sub-rule (a): Four `args:` entries in the Docker action directly interpolate attacker-controlled `inputs.*` expressions via `${{ }}` YAML template substitution before the container processes them. The offending lines are:
- `'${{ inputs.project }}'` — line 23
- `'${{ inputs.path }}'` — line 25
- `'${{ inputs.format }}'` — line 27
- `'${{ inputs.others }}'` — line 31

An attacker who controls these inputs (e.g. via `workflow_dispatch` or a calling workflow) can inject arbitrary content that is substituted into the YAML before execution. These values should be passed as environment variables and referenced safely, or the action should validate/sanitize inputs before use.

Locations:

- `action.yml:23`
- `action.yml:25`
- `action.yml:27`
- `action.yml:31`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, script-injection

**Notes:**

1. Pinned docker image from mutable ':latest' tag to immutable SHA digest: 'docker://owasp/dependency-check-action:latest@sha256:98d9c2f1ddd8c649e9b0b16cd22f0926136df2784a93697de2ccd9f9b491e923'. The docker:// scheme and :latest tag are preserved inline per requirements. 2. Fixed script injection by moving all four ${{ inputs.* }} expressions (project, path, format, others) from args: into an env: block under runs:, then referencing them as plain environment variables ($INPUT_PROJECT, $INPUT_PATH, $INPUT_FORMAT, $INPUT_OTHERS) in the args list. This prevents YAML template substitution of attacker-controlled values directly into the args array.

