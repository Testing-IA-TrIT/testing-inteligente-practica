# Record evidence for failed attempts

## Collect evidence

1. Read the errors, attachments and `error-context.md` for each failed attempt.
2. Find the evidence through attachment paths or the recorded test output folder. Use files from the run that the report describes.
3. Copy each available `error-context.md` in full and each failure screenshot to `e2e-evidence/<test-id>/` in the selected spec folder.
4. Name the files `error-context-attempt-<n>.md` and `screenshot-attempt-<n>.png`. Use the attempt number for `<n>`.
5. Mark missing evidence as unavailable. For traces and videos, record the source paths only.

## Write the failed attempt details

1. Put tests from the selected spec in `Failures`. Put tests from other specs in `Regressions`.
2. Include each test ID, all tags, the file and line, the errors, the page excerpt and the evidence links. Use relative Markdown links for copied evidence.
3. Find fenced YAML page trees in every section of `error-context.md`. Select only the `main` node and its descendants by indentation.
4. Include at most 40 lines in total, including the `main` node. Mark truncation outside the code block. If no `main` node exists, state that the page excerpt is unavailable.

## Check the report

1. Check the length of each excerpt.
2. Check that each evidence link opens a file in the selected spec folder.
3. Check that each file in `e2e-evidence/` has a link. Remove files that have no link.
