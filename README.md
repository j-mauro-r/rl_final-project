# Q-Learning Maze Solver (Final Project)

This project implements a **Reinforcement Learning (RL)** agent using **Q-Learning** to solve mazes represented as grid worlds with walls.

**Authors:** Nicolas Steven Lara Villa, Jersson Mauricio Rodríguez Aponte  
**Date:** November 2025

---

## Overview

The main notebook (`rl_final-project.ipynb`) includes:

- Maze parsing from `laberinto.txt` (stored in the repository root)
- Wall interpretation to block invalid moves between adjacent cells
- Automatic detection of:
  - **START**: first cell in column `0` with no wall on the left boundary
  - **GOAL**: first cell in the last column with no wall on the right boundary
- An RL environment (`MazeEnv`) with `reset()`, `step()`, and `render()`
- A `QLearningAgent` trained with an **ε-greedy** policy and epsilon decay
- Support for loading an existing **Q-table** (`.npy`) or training a new one if the file is missing/invalid

---

## Repository contents

- `rl_final-project.ipynb` — Main notebook (load/train/evaluate/render)
- `laberinto.txt` — Maze definition file
- `q_table.npy` — (Optional) Pre-trained Q-table saved as a NumPy array (file name configurable in the notebook)

---

## Maze file format (`laberinto.txt`)

The maze file uses this format:

1. Line 1: `n_rows n_cols`
2. Line 2: `k` (number of wall segments)
3. Next `k` lines: `x1 y1 x2 y2` (wall segment endpoints)

Wall segments are interpreted as horizontal/vertical walls and converted into blocked transitions between adjacent grid cells.

---

## Agent actions

The agent has 4 actions:

| Action | Name  |
|------:|-------|
| 0     | UP    |
| 1     | DOWN  |
| 2     | LEFT  |
| 3     | RIGHT |

Actions that leave the grid or cross a wall are treated as invalid.