# Alien Invasion

A 2D arcade shooter game built with Pygame, from Part II of Python Crash Course (Chapters 12-14).

## Gameplay

Control a spaceship at the bottom of the screen and shoot down waves of aliens before they reach you. Each wave moves faster than the last.

## Controls

| Key | Action |
|-----|--------|
| Left/Right Arrow | Move ship |
| Space | Fire bullet |
| Q | Quit game |
| Mouse Click | Start game (Play button) |

## Features

- Progressive difficulty (aliens speed up each level)
- Score tracking with high score
- Lives system (3 ships)
- Level indicator
- Full-screen mode option

## Project Structure

```
alien_invasion/
├── alien_invasion.py   # Main game loop and logic
├── settings.py         # Game configuration
├── ship.py             # Player ship class
├── alien.py            # Alien sprite class
├── bullet.py           # Bullet sprite class
├── button.py           # UI button class
├── game_stats.py       # Game statistics tracking
├── scoreboard.py       # Score display
└── images/
    ├── ship.bmp        # Player ship image
    ├── alien.bmp       # Alien image
    └── star_wars/      # Alternative sprites
```

## Requirements

```bash
pip install pygame
```

## Running the Game

```bash
python alien_invasion.py
```

## Configuration

Edit `settings.py` to customize:
- Screen dimensions
- Ship speed and lives
- Bullet speed and limits
- Alien speed and fleet behavior
- Full-screen mode
