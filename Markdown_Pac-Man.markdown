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

- **Maze**: A 28x31 grid defined in `initialmaze`, with walls (`#`), pellets (`.`), super pellets (`O`).
- **Pac-Man**: Moves arrow keys, wraps around screen edges, and collects pellets.
- **Ghosts**: Each ghost has unique behavior:
  - **Blinky**: Chases Pac-Man directly.
  - **Pinky**: Targets a position offset from Pac-Man.
  - **Inky**: Uses Blinky’s position and Pac-Man’s direction for targeting.
  - **Clyde**: Chases Pac-Man if far, scatters if close.
- **Power-Up**:
  - **Super Pellet (**`O`**)**: Makes ghosts frightened for 9 seconds, allowing Pac-Man to eat them for bonus points (200, 400, 800, 1600).

### Scoring

- Regular pellet: 10 points
- Super pellet: 50 points
- Eating ghosts: 200 \* 2^n points (n = number of ghosts eaten in sequence)
- Extra life at 5000 points
- High score saved to difficulty-specific files (`highscore_easy.txt`, `highscore_medium.txt`, `highscore_hard.txt`)

### Difficulty Levels

- **Easy (1)**: Ghost speed = 14
- **Normal (2)**: Ghost speed = 10
- **Hard (3)**: Ghost speed = 9, frightened speed = 15

## Local Setup Instructions

- Install GIT (if not installed)
  ```bash
    install git
    winget install --id Git.Git -e --source winget
    git --version
  ```
- Clone the Repo locally using your PC's powershell with the code:
  ```bash
     git clone https://github.com/username/repository.git
  ```
- Install Raylib Locally
  ```bash
    git clone https://github.com/raysan5/raylib.git
    cd raylib/src
    mingw32-make
  ```
- Compile the code
  ```bash
     gcc PACMAN_Final.c -o pacman.exe -Iraylib/src -Lraylib/src -lraylib -lopengl32 -lgdi32 -lwinmm
  ```
- Run the game
  ```bash
     .\pacman.exe
  ```
- Alternatively, go to the directory where the PACMAN_final application is located and direclty run without installing raylib and compiling the code.

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

## Improvements 
- Add WASD keys for input
- Increasing Speed (Speed Boost!)
- Adding Super Pellets like:
    - Freezing Ghosts for a set duration 
    - Making Ghosts Lazy (decreasing their speeds for some time) etc
  
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
- Screenshots have been included in the forked repo.

## Lab Group 

- Group Name: DSGO
- Members:
- Jay Patel
- Nikhil Gupta
- Pearl Tarawat
- Siddhant Sareen
