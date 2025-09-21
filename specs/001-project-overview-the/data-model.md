# Data Model

## Entities

### SudokuGrid
- **Purpose**: Represents the 9x9 Sudoku board
- **Fields**:
  - puzzle: 2D array (9x9) of initial numbers (0 for empty)
  - solution: 2D array (9x9) of correct numbers
  - userGrid: 2D array (9x9) of user inputs
  - annotations: 3D array (9x9x9) for notes (boolean per cell per number)
- **Relationships**: Contains 81 Cells
- **Validation**: Must be valid Sudoku format

### Cell
- **Purpose**: Represents a single cell in the grid
- **Fields**:
  - row: number (0-8)
  - col: number (0-8)
  - value: number (0-9, 0=empty)
  - isPreFilled: boolean
  - notes: array of booleans (9 elements for 1-9)
- **Relationships**: Belongs to SudokuGrid
- **Validation**: Value must be 0-9, notes only for user cells

### UserSettings
- **Purpose**: Stores user preferences
- **Fields**:
  - language: string ('ja' or 'en')
  - difficulty: string ('easy', 'medium', 'hard')
  - isAnnotationMode: boolean
  - selectedCell: {row, col} or null
- **Relationships**: None
- **Validation**: Language in ['ja', 'en'], difficulty in ['easy', 'medium', 'hard']

### PuzzleList
- **Purpose**: Stores available puzzles by difficulty
- **Fields**:
  - easy: array of SudokuGrid objects
  - medium: array of SudokuGrid objects
  - hard: array of SudokuGrid objects
- **Relationships**: Contains SudokuGrid objects
- **Validation**: At least one puzzle per difficulty

## State Transitions
- Game initialization: Load puzzle → Set userGrid to puzzle → Clear annotations
- Cell selection: Update selectedCell
- Number input: If annotation mode, toggle note; else set value
- Mode toggle: Switch isAnnotationMode
- Language change: Update UI text only
- New game: Select new puzzle → Reset state
