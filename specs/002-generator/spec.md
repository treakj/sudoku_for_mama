# Generator: Dynamic Puzzle Generator with Backtracking Algorithm

## Summary

Add a runtime puzzle generator using backtracking algorithm (based on https://www.101computing.net/backtracking-algorithm-sudoku-solver/) so the app can create unique, solvable puzzles per difficulty without relying on a static puzzle list. Maintain Japanese difficulty levels and senior-focused accessibility.

## Goals

- Generate full valid Sudoku solutions with randomized backtracking algorithm.
- Produce puzzles by removing numbers while ensuring exactly one solution.
- Support Japanese difficulty levels: 初級(36-46 clues), 中級(28-35 clues), 上級(17-25 clues).
- Integrate generator into existing game flow replacing static puzzle arrays.
- Maintain all accessibility features and Japanese interface.

## Acceptance Criteria

- The app generates unique puzzles for each difficulty level (初級/中級/上級).
- Generated puzzles follow all Sudoku rules and have exactly one solution.
- Puzzle generation completes within 500ms to maintain responsive UX.
- Fallback to static puzzles if generation fails or times out.
- All existing game features remain functional (annotations, highlighting, etc.).
- Console logging for generation performance and debugging.

## Constraints & Notes

- Keep root `index.html` as single source of truth with generator functions in `<script>` section.
- Performance target: <500ms generation time for smooth senior user experience.
- Graceful fallback: Use static puzzles if dynamic generation fails.
- Preserve existing Japanese UI and accessibility features.
- No external dependencies - vanilla JavaScript only.
