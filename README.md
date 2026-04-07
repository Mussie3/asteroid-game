# Asteroids Game

A classic Asteroids arcade game built with Python and Pygame.

## Gameplay

- Pilot a spaceship through an asteroid field
- Shoot and destroy asteroids — large asteroids split into smaller, faster ones
- Survive as long as you can; a single collision ends the game

### Controls

| Key | Action |
|-----|--------|
| W / S | Move forward / backward |
| A / D | Rotate left / right |
| Space | Shoot |

## Requirements

- Python 3.13+
- [uv](https://github.com/astral-sh/uv) (recommended) or pip

## Installation & Running

```bash
# Install dependencies
uv sync

# Run the game
python main.py
```

Or with pip:

```bash
pip install pygame==2.6.1
python main.py
```

## Project Structure

```
├── main.py            # Game loop and collision detection
├── player.py          # Player ship (movement, rotation, shooting)
├── asteroid.py        # Asteroid behavior and splitting
├── asteroidfield.py   # Asteroid spawning from screen edges
├── shot.py            # Player projectiles
├── circleshape.py     # Base class for all circular game objects
├── constants.py       # Game configuration (speeds, sizes, cooldowns)
└── logger.py          # Game state and event logging
```

## Architecture

All game objects inherit from `CircleShape`, which extends `pygame.sprite.Sprite` and provides position, velocity, and circle-based collision detection. Pygame sprite groups (`updatable`, `drawable`) manage the update/render lifecycle.

Asteroids spawn at random screen edges every 0.8 seconds in three sizes (small, medium, large). When shot, they split into two smaller asteroids with slightly rotated and faster trajectories. The smallest asteroids are destroyed outright.

## Logging

The game logs state snapshots and events (collisions, splits) to `game_state.jsonl` and `game_events.jsonl` for debugging and analysis.
