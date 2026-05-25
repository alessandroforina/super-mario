# Super Mario — Claude Code Project Guide

## Project Overview

A Python recreation of Super Mario Bros (World 1, Levels 1–3) built as a structured learning project.
Primary goals:
- Build a playable game using **pygame**
- Practice professional Python project habits: virtual environments, linting, formatting, code organization
- Learn iterative development: start rough, refine with tooling

## Tech Stack

- **Language:** Python 3.12+
- **Game library:** pygame (to be installed)
- **Formatter/linter:** ruff
- **Package management:** pip + venv (standard library)
- **Testing:** TBD

## Running the Game

```bash
python -m src
```

## Project Structure

```
super-mario/
├── CLAUDE.md
├── pyproject.toml
├── README.md
├── assets/
│   ├── images/
│   ├── sounds/
│   └── fonts/
├── saves/
├── src/
│   ├── __main__.py
│   ├── game.py
│   ├── hud.py
│   ├── entities/
│   │   ├── base.py
│   │   ├── playable_characters/
│   │   │   └── mario.py
│   │   ├── enemies/
│   │   │   ├── goomba.py
│   │   │   └── koopa.py
│   │   ├── blocks/
│   │   │   ├── ground.py
│   │   │   ├── brick.py
│   │   │   ├── question_block.py
│   │   │   └── pipe.py
│   │   └── items/
│   │       ├── coin.py
│   │       ├── mushroom.py
│   │       └── fire_flower.py
│   ├── systems/
│   │   ├── physics.py
│   │   ├── collision.py
│   │   └── camera.py
│   ├── levels/
│   │   ├── loader.py
│   │   ├── level_1_1.py
│   │   ├── level_1_2.py
│   │   └── level_1_3.py
│   └── persistence/
│       └── save_state.py
└── tests/
```

## Development Setup

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Code Style

- Formatter and linter: **ruff** (replaces black + flake8 + isort)
- Run before committing: `ruff check . && ruff format .`
- Line length: 88 (ruff default)
- No commented-out code in commits

## Key Design Decisions

- `src/` layout — prevents accidental import of uninstalled package during testing
- `entities/base.py` — single source of truth for `Sprite`, `StaticSprite`, `DynamicSprite`
- `playable_characters/` — extensible folder so other characters can be added later
- `blocks/` subfolder — ground, bricks, pipes, question blocks all share the same base class
- `persistence/` + `saves/` — save/load code separate from save data files
- Game library: TBD (pygame or lower-level alternative — decision deferred)

## Scope

Levels implemented: World 1-1, 1-2, 1-3 (original NES layout as reference)
Out of scope for v1: multiplayer, sound, full enemy roster beyond the first three levels
