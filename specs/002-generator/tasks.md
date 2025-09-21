# Tasks for Generator Feature

1. T001 - Add generator + solver functions to `index.html` (implement `generateSolution`, `solveCount`, `makePuzzleFromSolution`).
2. T002 - Wire `newGame()` to use generator by default; fallback to static `puzzles` if generator fails.
3. T003 - Add a tiny test harness `scripts/generator_test.ps1` that runs generator multiple times and validates uniqueness.
4. T004 - Update `quickstart.md` and `README.md` with generator usage.
5. T005 - Unit test: ensure `solveCount()` returns 1 for a curated sample puzzle.
6. T006 - Performance: measure and log generation time; if >1s on dev machine, add loading UI.
7. T007 - Push feature branch and open PR; include checklist in PR description for QA.
