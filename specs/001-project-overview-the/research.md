# Research Findings

## Language Switching Behavior
**Decision**: Language switch affects only UI elements (buttons, labels, messages). Puzzle data (numbers) remains unchanged as they are universal.

**Rationale**: Sudoku puzzles use numbers 1-9 which are the same in all languages. Switching language should not alter the game state to avoid confusion. UI text like "新しいゲーム" to "New Game" is sufficient.

**Alternatives Considered**: 
- Translating puzzle numbers: Rejected as it would complicate the game logic and confuse users.
- Storing puzzles in multiple languages: Rejected due to increased complexity and storage.

## Invalid Move Handling
**Decision**: Invalid moves (duplicate numbers in row/column/box) are highlighted with visual feedback but not blocked.

**Rationale**: Allows users to explore possibilities and learn from mistakes without frustration. Highlighting provides guidance without preventing input.

**Alternatives Considered**:
- Blocking invalid moves: Rejected as it might frustrate users trying to understand the rules.
- No feedback: Rejected as it defeats the purpose of assistance tools.

## Technology Choices
**Decision**: Vanilla HTML/CSS/JS with no frameworks.

**Rationale**: Keeps the app simple, fast-loading, and accessible without dependencies.

**Alternatives Considered**: React/Vue - Rejected for simplicity and no backend.

## Puzzle Storage
**Decision**: Predefined puzzles stored as arrays in JS.

**Rationale**: Client-side only, no backend needed.

**Alternatives Considered**: Generate puzzles dynamically - Rejected for complexity.
