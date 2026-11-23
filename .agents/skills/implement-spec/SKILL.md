---
name: implement-spec
description: Implements the back and front of a prescriptive spec in specs/, with unit tests for the service layer only. Use it to implement an existing spec, or when the user invokes /implement-spec.
---

# Implement a spec

Implement the back and the front of one spec. The result is an application that you can test.

## Input

1. Read the spec in `specs/<id>-<slug>/<id>.spec.md`.
2. If `solution-mode` is `descriptive`, explain that the spec documents existing behavior and stop. If `solution-mode` is absent, use `prescriptive`.
3. Read the code in `projects/back` and `projects/front` that is related to the spec.
4. Find the existing style: folders, names, layers and test files.
5. Make an assumption when the context gives a safe answer.
6. If you are not sure, ask the user. Propose your answer.

## Steps

1. For a `bug-fix` or `refactor`, run the service tests that the spec identifies for the baseline. Add the service baseline test first if the spec requires one. Record the result before you change the implementation.
2. Implement the **Back** steps if they specify work.
3. Implement the **Front** steps if they specify work.
4. Write any remaining unit tests required by the spec or the business rules.
5. Run `vp check`. If it fails, run `vp check --fix` and fix the remaining errors.
6. Run `npm test` in the root folder. Fix the code until all tests pass.
7. Stop when `vp check` and `npm test` pass.

## Rules

- Each EARS criterion (`R1`, `R2`, ...) is a goal that you can verify.
- Each business rule is a goal that you can verify.
- Write the minimum code that satisfies the spec.
- Do not add speculative code. Do not add a feature, an option or an abstraction that the spec does not need.
- Use the existing style and the existing structure.
- Do not implement the **E2E** steps.
- Write unit tests only for the service layer (`logic`).
- Do not test routes, controllers, components or infrastructure.

## Output

1. Report each criterion (`R1`, `R2`, ...) and the code that satisfies it.
2. Report the baseline results if you ran the baseline tests.
