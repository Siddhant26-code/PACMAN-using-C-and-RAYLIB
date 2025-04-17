# Pac-Man Markdown File

## Overview

This is a C implementation of the classic Pac-Man game using the Raylib library. The game includes a maze, Pac-Man, four ghosts (Blinky, Pinky, Inky, Clyde), pellets, super pellets, and special power-ups.

##  About Game

### Screens

- **Describe**: Shows character information and point values.
- **Difficulty**: Allows selection of Easy, Normal, or Hard mode.
- **Diff_Selection**: Confirms difficulty choice.
- **Loading**: Displays a loading screen.
- **Gameplay**: Main game screen with maze and interactions.
- **RemainingLives**: Shows remaining lives after Pac-Man's death.
- **GameOver**: Displays when lives run out, with replay option.
- **GameWin**: Appears when all pellets are collected, with replay option.

### Gameplay Elements

- **Maze**: A 28x31 grid defined in `initialmaze`, with walls (`#`), pellets (`.`), super pellets (`O`), speed boost (`S`), freeze (`F`), and lazy ghost (`L`) pellets.
- **Pac-Man**: Moves using W,A,S,D or arrow keys, wraps around screen edges, and collects pellets.
- **Ghosts**: Each ghost has unique behavior:
  - **Blinky**: Chases Pac-Man directly.
  - **Pinky**: Targets a position offset from Pac-Man.
  - **Inky**: Uses Blinky’s position and Pac-Man’s direction for targeting.
  - **Clyde**: Chases Pac-Man if far, scatters if close.
- **Power-Ups**:
  - **Super Pellet (**`O`**)**: Makes ghosts frightened for 9 seconds, allowing Pac-Man to eat them for bonus points (200, 400, 800, 1600).
  - **Speed Boost (**`S`**)**: Doubles Pac-Man’s speed for 5 seconds.
  - **Freeze (**`F`**)**: Freezes ghosts for 5 seconds.
  - **Lazy Ghost (**`L`**)**: Makes one ghost move randomly for 7 seconds.

### Scoring

- Regular pellet: 10 points
- Super pellet: 50 points
- Speed boost pellet: 50 points
- Freeze pellet: 50 points
- Lazy ghost pellet: 50 points
- Eating ghosts: 200 \* 2^n points (n = number of ghosts eaten in sequence)
- Extra life at 5000 points
- High score saved to difficulty-specific files (`highscore_easy.txt`, `highscore_medium.txt`, `highscore_hard.txt`)

### Difficulty Levels

- **Easy (1)**: Ghost speed = 14
- **Normal (2)**: Ghost speed = 10
- **Hard (3)**: Ghost speed = 9, frightened speed = 15

## Code Structure

### Key Data Structures

- **Direction**: Enum for movement (STOP, UP, DOWN, LEFT, RIGHT).
- **Vector2Int**: Struct for grid positions (row, col).
- **GameScreen**: Enum for game states.
- **Maze**: 2D char array (28x31) for the game map.

### Important Variables

- `pos`: Pac-Man’s position (Vector2).
- `blinkyPos`, `pinkyPos`, `inkyPos`, `clydePos`: Ghost positions (Vector2Int).
- `score`, `lives`, `hscore`, `filescore`: Track game progress.
- `superPelletEaten`, `isSpeedBoostActive`, `isFreezeActive`, `isLazy*`: Track power-up states.
- `ghostSPEED`, `frightenedSPEED`, `SPEED`: Control movement speeds.

### Key Functions

- **drawMaze**: Renders the maze, pellets, and power-ups.
- **updatePacmanPosition**: Handles Pac-Man’s movement and screen wrapping.
- **checkCollisionWithPellets**: Manages pellet collection and power-up activation.
- **moveGhost**: Moves ghosts using a shortest-path algorithm.
- **findShortestPath**: BFS algorithm for ghost pathfinding.
- **ghostcollisionpacman**: Detects collisions between Pac-Man and ghosts.
- **drawPacman**, **drawScore**, **drawlives**: Render game elements.

## Assets

- **Sprites**: Pac-Man animations, ghost textures, frightened/eyes states.
- **Audio**: Intro music, munch sound, siren, super pellet sound, death sound.
- **Textures**: Game over, game win, and loading screens.

## Game Loop

- Runs at 60 FPS.
- Handles screen transitions, input, and game logic.
- Updates Pac-Man, ghosts, and power-up timers.
- Checks for win (no pellets left) or loss (no lives).

## Notes

- The game uses Raylib for graphics and audio.
- Ghosts switch between scatter (6 seconds) and chase modes.
- Frightened ghosts move randomly and flash white near the end of the effect.
- High score persists across sessions per difficulty.
- Pac-Man’s death triggers an animation and resets positions.

## Lab Group 

- Group Name: DSGO
- Members:
- Jay Patel
- Nikhil Gupta
- Pearl Tarawat
- Siddhant Sareen
