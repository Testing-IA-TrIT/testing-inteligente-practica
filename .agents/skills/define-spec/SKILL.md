---
name: define-spec
description: Writes one spec for existing behavior, a new feature, a bug fix, a refactor or a behavior change. Use it when you write a spec in specs/, or when the user invokes /define-spec.
---

# Define a spec

Write one `spec.md` for each request.

## Input

1. Read the related specs in `specs/` and the evidence from the user.
2. When the request concerns existing behavior, read the relevant code and tests.
3. Use the details the user gives. If a required detail is missing and you cannot make a safe assumption, ask one closed question. Propose an answer.

## Steps

1. Set `id` to the next free `S0000` number. Count only the folders `S*`. Set `name` and `slug`.
2. Set `type` from the request.
   - `feature` adds a capability or documents an existing capability.
   - `bug-fix` restores the expected result of an existing rule.
   - `refactor` changes the implementation and preserves observable behavior.
   - `change` modifies an existing rule or contract.
3. Set `solution-mode` to `descriptive` when the user asks what the system does today. Use `prescriptive` when the user asks for an implementation change. A new feature uses `feature` and `prescriptive`.
4. Follow the [rules](#rules) for the selected `solution-mode` and `type`.
5. Follow the [writing guide](resources/write-spec.md) and use [spec.template.md](assets/spec.template.md) to draft the spec. Apply the rules from the selected guides to the same draft.

## Rules

- For `descriptive`, read [Document existing behavior](resources/descriptive.md).
- For `bug-fix`, read [Specify a bug fix](resources/bug-fix.md).
- For `refactor`, read [Specify a refactor](resources/refactor.md).
- For `change`, read [Specify a behavior change](resources/change.md).
- Keep the spec shorter than 100 lines.

## Output

1. Check that `type` and `solution-mode` match the request. Check that each EARS criterion links to a user story.
2. Show the spec to the user.
3. Save it in `specs/<id>-<slug>/spec.md` only after the user confirms.
