![pypi](https://img.shields.io/badge/pypi-v0.4.6-orange)
![python](https://img.shields.io/badge/python-2.7%20%7C%203.7%20%7C%203.8%20%7C%203.9%20%7C%203.10-blue)
![test](https://img.shields.io/badge/Test-passing-brightgreen)

# Othello AI — Minimax + Alpha-Beta Pruning


This project implements an AI that plays Othello (Reversi) using the Minimax algorithm enhanced with Alpha-Beta Pruning for efficient decision-making.
The goal is to provide a clean, readable, and expandable implementation suitable for learning, experimenting, or integrating into a larger game system.

## Features

  AI opponent powered by Minimax
  
  Faster decision-making using Alpha-Beta pruning
  
  Configurable search depth
  
  Human vs AI gameplay
  
  Modular design (board logic, AI logic, game engine separated)
  
  Easy to extend with better heuristics or GUI

## Installation
1. Clone the repository

```bash
git clone https://github.com/USERNAME/REPO.git
cd REPO
```
2. Install dependencies
```bash
pip install -r requirements.txt
```

## How to Play
Run the main game:
```bash
python main.py
```
You can configure:

- Who goes first

- AI search depth

- Display options

## Project Structure
```arduino
REPO/
│── ai/
│   ├── minimax.py
│   ├── evaluator.py
│── game/
│   ├── board.py
│   ├── logic.py
│── assets/
│   └── demo.png   (optional demo image)
│── main.py
│── requirements.txt
│── README.md
```

## Minimax + Alpha-Beta Example
```python
def minimax(board, depth, maximizing, alpha, beta):
    if depth == 0 or board.is_terminal():
        return evaluate(board)

    if maximizing:
        value = float('-inf')
        for move in board.valid_moves():
            new_board = board.apply_move(move)
            value = max(value,
                        minimax(new_board, depth - 1, False, alpha, beta))
            alpha = max(alpha, value)
            if alpha >= beta:
                break
        return value
    else:
        value = float('inf')
        for move in board.valid_moves():
            new_board = board.apply_move(move)
            value = min(value,
                        minimax(new_board, depth - 1, True, alpha, beta))
            beta = min(beta, value)
            if alpha >= beta:
                break
        return value
```
## Demo
