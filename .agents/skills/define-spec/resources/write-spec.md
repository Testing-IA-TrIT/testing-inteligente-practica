# Write the spec

1. In **Problem**, state the objective in one or two short sentences. Add the relevant evidence.
2. In **User stories**, write 1 to 3 stories. Use `US1`, `US2` and `US3`.
3. In **Business rules**, write fewer than 8 rules. Use RuleSpeak (`A <term> must ...`).
4. In **Out of scope**, list the items outside the request.
5. In **Solution**, write fewer than 10 items for each part.
   - **Back** covers API resources, endpoints, status codes, checks and `logic` rules.
   - **Front** covers pages, forms, fields, messages and navigation.
   - **E2E** covers seed data, unique data and main flows.
   - In `prescriptive` mode, state the actions to take. Use `None` for a part with no work.
6. In **Verification**, write 1 to 9 EARS criteria for observable results. In `prescriptive` mode, cover the target results.

## EARS criteria

- Give each criterion a unique code in the spec. Use `R1`, `R2` and so on.
- Assign each criterion to one story. If a criterion applies to two stories, write a separate criterion for each.
- Put the story code after the criterion code, as in `R3 (US2)`.
- Give each story one or more criteria.
- Number the criteria in story order. Start the criteria for `US1` at `R1`.
- Use one of these EARS patterns.
  - **Ubiquitous** `The system shall ...`
  - **Event** `When <trigger>, the system shall ...`
  - **State** `While <state>, the system shall ...`
  - **Unwanted** `If <condition>, then the system shall ...`
  - **Option** `Where <feature>, the system shall ...`
- Write each criterion as a checkbox, as in `- [ ] R1 (US1): When ..., the system shall ...`.
