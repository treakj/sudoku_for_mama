# Generator: randomized puzzle generator with uniqueness check

## Summary

Add a runtime puzzle generator and solver so the app can create unique, solvable puzzles per difficulty without relying on a static puzzle list.

## Goals

- Generate full valid Sudoku solutions with randomized backtracking.
- Produce puzzles by removing numbers while checking uniqueness (exactly 1 solution).
- Allow difficulty tuning (Easy/Medium/Hard) by controlling minimum clue counts and removal strategies.
- Integrate generator into existing `newGame(difficulty)` flow with a fallback to static puzzles.

## Acceptance Criteria

- The app can start a new game using `newGame('easy'|'medium'|'hard')` that uses the generator.
- Generated puzzles are valid and have exactly one solution.
- Unit-style tests (small scripts) included to run generator+solver quickly.
- Documentation added to `specs/002-generator/quickstart.md` showing how to run and test generator.

## Constraints & Notes

- Keep root `index.html` as single source of truth. Implement generator functions inside a clear region in `<script>`.
- Keep performance responsive: generation should complete in < 1s on typical desktop. If it takes longer, add a small loading screen.
