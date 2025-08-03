# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

PyxPrime is a prime factorization game built with the Pyxel game engine. Players need to factor numbers by entering prime factors (2, 3, 5, 7) within a 30-second time limit.

## Development Setup

```bash
# Install dependencies
pip install pyxel

# Run the game
python main.py
```

**Requirements**: Python 3.6+ and pyxel 2.4.10+

**Note**: If you get an error about old Pyxel resource file, the `assets/pyxprime.pyxres` file needs to be re-saved with the latest Pyxel editor. The game code has been updated to work with Pyxel 2.4.10+.

## Architecture

### Core Components

- **main.py**: Contains the `Main` class that handles the complete game loop including initialization, game state management, input handling, and rendering
- **status.py**: Defines the `Status` enum with three game states: TITLE, GAMING, TIMEUP
- **common.py**: Constants for UI layout, colors, timing, sprite coordinates, and file paths
- **assets/pyxprime.pyxres**: Pyxel resource file containing sprites for numbers and operators

### Game Logic Flow

The game follows a state-based architecture:

1. **TITLE**: Initial screen waiting for space key to start
2. **GAMING**: Active gameplay with question generation, input handling, and scoring
3. **TIMEUP**: End screen showing final score and high score comparison

### Key Game Mechanics

- Questions are randomly generated composite numbers made from prime factors 2, 3, 5, 7
- Players input prime factors using number keys (2, 3, 5, 7)
- Division is performed when Enter is pressed - if the result equals 1, the question is solved
- Visual feedback through area blinking for question updates and wrong answers
- High score persistence in `pyxprime.dat` file

### File Structure

- Game state and logic: `main.py:8-253`
- UI constants and layout: `common.py:1-34`  
- Game state enumeration: `status.py:4-6`
- Visual assets: `assets/pyxprime.pyxres`

### Input Controls

- Number keys (2, 3, 5, 7): Add prime factors to answer
- Space: Clear current answer
- Backspace: Remove last entered factor
- Enter: Submit answer and attempt division

## Game Data

- **High Score Storage**: Persisted in `pyxprime.dat` file in the project root
- **Game Assets**: Sprites and visual resources stored in `assets/pyxprime.pyxres`

## Version History

- **Version 2.0.0**: Current release with Pyxel 2.4.10+ compatibility updates
- **Version 1.0.0**: Initial release