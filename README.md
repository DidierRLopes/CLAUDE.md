# CLAUDE.md

## 1. Global scope & boundaries

- NEVER run any linters unless explicitly asked.
- NEVER write unit tests unless explicitly asked.
- NEVER refactor code that is outside the scope of the request.
- NEVER run the build; I will run it locally.

## 2. Alignment before starting

- Restate my goal in your own words.
- List unknowns and ask clarifying questions until the request is unambiguous.
- Wait for my confirmation before proceeding.

## 3. Implementation planning

### 3.1 Plan of attack

- Create a step-by-step plan with small, verifiable commits.
- Include a rollback plan.
- Wait for my go-ahead before writing code.

### 3.2 Change surface

- List all files you expect to modify.
- If you are going to add 1 or more new files ask me permission to do so and explain what is the purpose of each of the files created. And why you couldn't use the others available.
- If you are going to delete 1 or more files ask me permission to do so and tell me what the file used to do and why you want to get rid of it.

### 3.3 Edge cases list

- Enumerate edge cases, failure modes, and concurrency/race concerns.
- State how each will be handled.

### 3.4 Testing strategy

- Assume I will run tests/builds. Do not run the build.
- Add lightweight debug hooks (console.log or equivalent) at key points so I can verify behavior quickly.
- Outline what to test and expected outputs, but only include actual tests if I explicitly ask.

### 3.5 Reuse before rebuild

- Identify existing utilities/hooks/services to reuse.
- If introducing a new abstraction, justify why reuse isn’t sufficient.

### 3.6 MVP first (divide to conquer)

- Propose a simplistic first pass to validate direction (minimal interface, happy path).
- Plan the follow-up phases to complete the full implementation after MVP is confirmed.

## 4. Step phased plan (detailed prompt)

Use the agreed Design/PRD, that we iterated together, as the single source of truth. Before coding, produce a 5–8 step phased plan. Each phase specifies goals, files to touch, and, when helpful, tiny code diffs/pseudocode (<15 lines). Keep phases minimal, shippable, and verifiable.

Deliverables before coding:
- a. Goal restatement & acceptance criteria.
- b. Repo scan & reuse targets.
- c. Implementation plan (5–8 phases) with file changes and small diffs.
- d. Testing strategy with debug logs I can use.
- e. Risks & rollback.
- f. Clarifying questions if any ambiguity remains.

## 5. Code style & comments

- Avoid line-by-line comments.
- Comment only where logic is non-obvious.

## 6. During execution

- If blocked or uncertain, stop and present 2–3 options with pros/cons; confirm before proceeding.
- Stick to the plan and scope; confirm any scope expansion first.
- Keep diffs small and mapped to phases; include the debug logs defined in 3.4.
