# Tasks for Feature: Web-Based Sudoku Game for Seniors

Feature: Web-Based Sudoku Game for Seniors  
Branch: `001-project-overview-the`  
Spec: `c:/Users/treak/Coding/sudoku_for_mom2/specs/001-project-overview-the/spec.md`

Instructions: Each task is actionable and specific. Tasks marked [P] can be worked on in parallel. Paths are absolute to the repository root.

T001 — Project skeleton and README (setup)
- Description: Create `index.html` with basic HTML5 skeleton and a placeholder header and main sections. Add a brief `README.md` describing how to open the file in a browser.
- Files/paths to create:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
  - `c:/Users/treak/Coding/sudoku_for_mom2/README.md`
- Dependencies: none
- Notes: Keep structure minimal; this file will be expanded by later tasks.

T002 — Add CSS layout and responsive grid (core)
- Description: In `index.html`, add a `<style>` block that defines layout styles for header, main area, and control panel. Implement responsive layout using CSS Grid/Flexbox and relative units (rem, vh, vw).
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T001 completed
- Notes: Use high-contrast styles and large default font sizes.

T003 — Implement static 9x9 grid markup and cell classes (core) [P]
- Description: Add the HTML structure for a 9x9 grid (81 cell elements) with appropriate classes and data attributes (`data-row`, `data-col`) so JS can target them.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T002
- Notes: Cells should include a container for large number and a mini-grid for annotations.

T004 — Implement `gameState` data structures and puzzles array (core) [P]
- Description: Add a `<script>` block with `gameState` object structure and a `puzzles` object containing at least one puzzle per difficulty (easy/medium/hard). Include an example puzzle and its solution.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T001
- Notes: Follow `data-model.md` shapes (puzzle, solution, userGrid, annotations, selectedCell, isAnnotationMode).

T005 — Implement `renderBoard()` and initial rendering (core)
- Description: Implement `renderBoard()` to read `gameState.puzzle` and `gameState.userGrid` and populate the DOM grid cells. Visually distinguish pre-filled numbers.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T003, T004
- Notes: Called by `init()` after selecting a puzzle.

T006 — Implement `handleCellClick()` and selection highlighting (core) [P]
- Description: Add event listeners to cells to update `gameState.selectedCell` and visually highlight row/column/box and the selected cell.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T003, T005
- Notes: Highlighting should be subtle (light grey or blue background).

T007 — Implement number pad UI and `handleNumberClick()` (core) [P]
- Description: Add a visible number pad (1-9) and wire clicks to `handleNumberClick(number)`. In Normal Mode, place the selected number into the selected cell if it's not pre-filled.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T002, T003, T005
- Notes: User-entered numbers should appear in a different color (e.g., dark blue) than pre-filled bold black numbers.

T008 — Implement Eraser (`handleErase()`) and UI button (core)
- Description: Add a large "消去" button that clears the selected cell's user-entered value or notes.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T007
- Notes: Should not clear pre-filled numbers.

T009 — Implement Annotation Mode toggle and mini-grid interaction (core)
- Description: Add a toggle for "メモモード". When enabled, number pad inputs toggle small notes within the selected cell's mini-grid.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T003, T004, T007
- Notes: Tapping a note again removes it.

T010 — Implement number & cell highlighting behaviors (core)
- Description: When a number is selected on the pad or a cell with a number is selected, highlight all matching numbers on the board. When a cell is selected, highlight its row, column, and 3x3 box.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T005, T006, T007
- Notes: Use soft colors (light yellow for number matches) and subtle backgrounds for row/col/box.

T011 — Implement `checkWinCondition()` and completion message (core)
- Description: Implement function to compare `userGrid` with `solution`. When solved correctly, display a large friendly message "おめでとうございます！".
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T004, T005, T007
- Notes: No timers or scores.

T012 — Visual feedback for invalid moves (UX)
- Description: When a user places a number that violates Sudoku rules (duplicate in row/col/box), visually mark the cell(s) (e.g., red outline) but allow the move.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T007, T010
- Notes: Provide a brief accessible explanation (tooltip or aria-live) in Japanese.

T013 — Language selector and UI translations (polish) [P]
- Description: Add a language selector with 日本語/English options. Switch UI text without altering game state. Default to Japanese.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T001, T005
- Notes: Keep translations inline; small JSON map of strings is fine.

T014 — Accessibility and keyboard support (polish)
- Description: Ensure large focus outlines, ARIA labels for controls, and keyboard navigation (arrow keys to move selection, number keys to input).
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T005, T006, T007
- Notes: Prioritize screen-reader friendly labels and high-contrast visuals.

T015 — Populate puzzles for each difficulty (data)
- Description: Add at least 3 puzzles per difficulty level into the `puzzles` array in JS.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T004
- Notes: Use known valid puzzles; include solutions.

T016 — Manual test scenarios and quickstart check (test) [P]
- Description: Run the quickstart scenarios in `specs/.../quickstart.md` and document any issues found; create a small `TEST_REPORT.md` with pass/fail for each scenario.
- Files/paths to create/edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/specs/001-project-overview-the/TEST_REPORT.md`
- Dependencies: T011, T013, T014
- Notes: Manual testing only.

T017 — Polish UI: colors, fonts, spacing, and mobile layout (polish)
- Description: Tune fonts (Noto Sans JP recommended), spacing, button sizes, and ensure grid scales well on tablet screens.
- Files/paths to edit:
  - `c:/Users/treak/Coding/sudoku_for_mom2/index.html`
- Dependencies: T002, T014
- Notes: Use rem and vw/vh units.

T018 — Final review & commit (wrap-up)
- Description: Ensure all files added/modified are committed on branch `001-project-overview-the`. Update `specs/.../progress` if present.
- Files/paths to check:
  - All files modified above
- Dependencies: All tasks complete
- Notes: Provide a short commit message and push the branch.


Parallel task grouping examples:
- Group A [P]: T003, T004, T007 (independent file edits in `index.html` but can be done together if coordinated)
- Group B [P]: T013, T016, T017 (polish tasks that don't block core logic)


Task numbering and execution notes:
- Follow TDD-ish order: create tests/verification steps in T016 where applicable before T011 is finalized.
- Tasks touching the same file (`index.html`) should be coordinated; consider branches or small commits per logical change.


---
Generated by /tasks command based on plan and available docs.
