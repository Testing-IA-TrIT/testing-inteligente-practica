# Write the features for a spec

## Input

1. Read `specs/<id>-<slug>/<id>.spec.md`. Find the user stories (`US1`, `US2`, ...) and the EARS criteria (`R1`, `R2`, ...).
2. Find the story of each criterion. Read the story code after the criterion code, as in `R3 (US2)`.
3. If a criterion has no story or code, ask the user. Propose an answer in the question.

## Steps

1. Write one `.feature` file for each user story. Use [the spec template](../assets/spec.user-story.template.feature).
2. Write the spec path in the first line, as in `# Spec: specs/<id>-<slug>/<id>.spec.md`.
3. Use the story code and title in `Feature: [US1] ...`. Write the `As a`, `I want to` and `So that` lines from the story.
4. Put the preconditions that all scenarios in the story share in `Background`.
5. Write one scenario for each EARS criterion of the story. Use one criterion per scenario.
   - Start the scenario name with the criterion code, as in `Scenario: [R1] Add a valid rocket`.
   - Write the trigger of the criterion in `When`.
   - Write the response of the criterion in `Then`.
   - Use `Scenario Outline` and `Examples` only when the criterion has more than one input.
6. Keep the scenarios in the order of the criteria.
