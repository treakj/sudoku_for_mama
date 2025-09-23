# Data Model: Dynamic Puzzle Generation

## Core Entities

### PuzzleGenerator
**Purpose**: Core component for creating Sudoku puzzles using backtracking algorithm
**Fields**:
- `currentGrid`: 9x9 array representing puzzle state during generation
- `solutionGrid`: 9x9 array representing complete solved puzzle
- `difficultySettings`: Object containing clue targets per difficulty level

**Methods**:
- `generatePuzzle(difficulty)`: Main entry point for puzzle creation
- `generateFullGrid()`: Creates complete valid Sudoku using backtracking
- `removeCluesForDifficulty(difficulty)`: Systematically removes cells to reach target
- `validateUniqueSolution()`: Ensures puzzle has exactly one solution

### ValidationEngine  
**Purpose**: Validates puzzle correctness and solution uniqueness
**Fields**:
- `testGrid`: Working copy of grid for validation testing
- `solutionCount`: Counter for tracking multiple solutions

**Methods**:
- `isValidPlacement(row, col, number)`: Checks Sudoku rules compliance
- `hasUniqueSolution(puzzle)`: Verifies exactly one solution exists
- `countSolutions(puzzle)`: Returns number of possible solutions
- `isValidSudoku(grid)`: Validates complete grid follows all rules

### DifficultyController
**Purpose**: Manages difficulty-specific parameters and clue removal strategies
**Fields**:
- `clueTargets`: Map of difficulty to target clue counts
  - `初級`: 36-46 clues
  - `中級`: 28-35 clues  
  - `上級`: 17-25 clues
- `removalStrategy`: Current strategy for cell removal ordering

**Methods**:
- `getTargetClues(difficulty)`: Returns target range for difficulty
- `getRemovalOrder()`: Determines optimal order for cell removal
- `validateDifficulty(puzzle, difficulty)`: Confirms appropriate challenge level

### PuzzleState
**Purpose**: Data structure representing current puzzle configuration
**Fields**:
- `puzzle`: 9x9 array with 0 for empty cells, numbers 1-9 for filled
- `solution`: 9x9 array with complete solution
- `metadata`: Object containing generation info
  - `difficulty`: Selected difficulty level
  - `clueCount`: Number of pre-filled cells
  - `generationTime`: Time taken to generate
  - `attempts`: Number of generation attempts

**State Transitions**:
- Empty → Generating → Complete → Failed (with fallback)

### GenerationConstraints
**Purpose**: Parameters and limits for puzzle generation process
**Fields**:
- `maxGenerationTime`: 500ms timeout limit
- `maxAttempts`: 3 attempts before fallback
- `minClues`: 17 (mathematical minimum for unique Sudoku)
- `maxClues`: 50 (maximum for reasonable difficulty)

**Validation Rules**:
- All difficulty targets must be >= minClues
- Generation time must not exceed maxGenerationTime
- Must maintain existing game state structure compatibility

## Integration with Existing System

### gameState Object Extensions
Current structure maintained with additions:
```javascript
gameState = {
    // Existing fields preserved
    puzzle: Array(9).fill().map(() => Array(9).fill(0)),
    solution: Array(9).fill().map(() => Array(9).fill(0)),
    userGrid: Array(9).fill().map(() => Array(9).fill(0)),
    
    // New fields for generation
    generation: {
        isGenerating: false,
        lastGenerationTime: 0,
        difficulty: '初級',
        fallbackUsed: false
    }
}
```

### API Contract
Replace existing static puzzle loading with dynamic generation:
- `loadNewGame(difficulty)` → calls `generatePuzzle(difficulty)`
- Maintain same return structure for compatibility
- Add generation status indicators if needed

## Relationships
- PuzzleGenerator uses ValidationEngine for solution checking
- DifficultyController provides parameters to PuzzleGenerator  
- PuzzleState holds results from all components
- GenerationConstraints govern all operations
- All components integrate with existing gameState object