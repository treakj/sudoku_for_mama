# GitHub Copilot Instructions for Sudoku Game

## Project Overview
Web-based Sudoku game for seniors with Japanese default, large grid, annotation tools.

## Technology Stack
- HTML5, CSS3, JavaScript ES6+
- Single-page application
- No frameworks or backend

## Key Components
- gameState: Central state object
- renderBoard(): Updates DOM
- Event handlers for user interactions
- Puzzle data stored as arrays

## Coding Guidelines
- Use vanilla JS, no libraries
- Relative units (rem, vh, vw) for responsiveness
- High contrast colors for accessibility
- Japanese text for UI elements
- Modular functions for game logic

## File Structure
- index.html: Complete app in one file
- CSS in <style> tag
- JS in <script> tag

## Recent Changes
- Initial setup for Sudoku game
- Spec and plan completed
- Dynamic puzzle generation with backtracking algorithm planned
- 5-phase generation process: full grid → cell removal → validation → difficulty calibration
- Target clue counts: 初級(36-46), 中級(28-35), 上級(17-25)
- Performance requirement: <500ms generation time
- Fallback to static puzzles if generation fails
