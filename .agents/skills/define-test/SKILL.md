---
name: define-test
description: Writes the Gherkin .feature files of a spec or a journey. A spec has one .feature for each user story and one scenario for each EARS criterion. A journey has one .feature. Uses the templates in assets/. Use it when you write .feature files, or when the user invokes /define-test.
---

# Define the features

Write Gherkin `.feature` files for one spec or one journey.

## Input

1. Get the code from the user. The code decides the mode. `S` is a spec. `J` is a journey.
2. If the user gives the code, do not ask for it again.

## Steps

1. For an `S` code, follow [the spec guide](resources/spec-steps.md).
2. For a `J` code, follow [the journey guide](resources/journey-steps.md).

## Rules

- Use Gherkin keywords in English: `Feature`, `Background`, `Scenario`, `Scenario Outline`, `Given`, `When`, `Then`, `And`, `Examples`.
- Use only the stories and the rules that exist. Do not invent rules.
- Obey the file and code rules E1 in [e2e-rules.md](../implement-test/references/e2e-rules.md).
- Do not write tests. Do not write application code.

## Output

1. Show the features to the user.
2. Wait for the user to confirm.
3. Save each feature in its folder (E1) only after the user confirms.
