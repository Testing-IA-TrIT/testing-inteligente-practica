---
name: spec-builder
description: Writes a spec through define-spec. Runs implement-spec after approval for a prescriptive spec. Use it to define existing behavior or implement a request, or when the user invokes /spec-builder.
---

# Build a spec

Coordinate the skills that write a spec and implement it when required.

## Input

1. Use the request from the user. Ask for it if it is missing.

## Steps

1. Run [define-spec](../define-spec/SKILL.md) with the request.
2. Stop and ask the user to approve the spec. This is the pause of `define-spec`. Do not ask again.
3. If the user does not approve, change the spec and ask again. Do not continue.
4. If the approved spec has `solution-mode: descriptive`, report its path and stop.
5. Run [implement-spec](../implement-spec/SKILL.md) with the approved spec.

## Rules

- Run the skills in order, in this conversation. Do not use subagents.
- Obey the Input, Steps, Rules and Output of each skill.
- Stop for approval only once, at step 2. Do not add other pauses.
- A skill can still ask a closed question when a data item is missing.
- If a skill fails, stop and report the failure. Do not run the next skill.

## Output

1. The path of the spec: `specs/<id>-<slug>/<id>.spec.md`.
2. The output of `implement-spec` when it runs.
