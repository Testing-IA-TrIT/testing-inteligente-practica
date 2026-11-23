---
name: detect-bugs
description: Runs Playwright tests for one spec or the full suite and writes an evidence report. Use it to check an existing spec, or when the user invokes /detect-bugs.
---

# Run E2E tests

Run the selected tests. Record results and evidence without diagnosis or repairs.

## Input

1. Read `AGENTS.md` and `e2e/playwright.config.ts`.
2. Get the spec code, for example `S0005`, and the scope: one spec or the full suite.
3. If an input is missing, ask one closed question at a time.
4. Find the matching `specs/<spec>-<slug>/` folder.
5. Read the [report template](assets/e2e-report.template.md).

## Steps

1. Run the selected command from the root.
   For one spec, use `npm run test:e2e -- --grep "@<spec>"`.
   For the full suite, use `npm run test:e2e`.
   The command stops the servers of `npm start`, empties the database and starts the back and the front.
   Record the command, start time and exit code.
   If the servers do not start, stop and report the command output.
2. Read `e2e/test-results/results.json` from this run.
   Reject a missing, invalid or stale result file.
   Read nested suites, test tags, result attempts and run errors.
3. Assign each test its rule tag as its ID, without `@`.
   For duplicate rule tags, add `-1`, `-2` and subsequent numbers.
   Assign suffixes in file, line and column order across all selected tests.
   Keep one ID across retries.
   If a rule tag is missing, use the Playwright test ID and record the missing tag.
4. Remove the previous `e2e-evidence/` from the selected spec folder.
   Verify that its resolved path is inside that folder before removal.
   Repeat this step for each new run before you copy evidence.
5. If any test attempt failed, read the [failure evidence guide](resources/failure-evidence.md).
   Follow it for each failed attempt, including attempts of tests that pass on retry.
6. Replace `e2e-report.md` in the selected spec folder with the report.
   Use the template and the [output rules](#output).
   Check the counts and test IDs. For failed attempts, apply the checks in the evidence guide.

## Rules

- Do not diagnose, repair, or change tests, code or configuration.
- Record observed clues only.
- Remove ANSI escape sequences from reported errors.
- Record failed retry attempts, flaky outcomes and run errors.
  Do not classify skipped tests or zero selected tests as a complete pass.

## Output

1. Save `specs/<spec>-<slug>/e2e-report.md`.
2. For a complete pass, keep only the date, command and result in the report.
   Reply with one line.
3. Include run errors even when no test result exists.
4. Report an incomplete run as incomplete.
   Do not reuse results or evidence from an earlier run.
