# Connect Four AI Agent

A Connect Four AI agent developed as part of an **Artificial Intelligence course project**.

The project implements an autonomous game-playing agent using **Minimax Search with Alpha-Beta Pruning**. The agent evaluates possible future game states using a custom heuristic evaluation function and selects a move based on the estimated quality of each position.

> **Project Scope:** My contribution to the original course project was the AI decision-making component presented in this repository. The complete game platform and interface were developed separately and are not included here.

## Overview

The goal of this project was to implement an AI agent capable of playing Connect Four against another player through an existing game platform.

The agent maintains its own representation of the game board, processes the opponent's moves, searches possible future states, and selects the next move using a depth-limited Minimax algorithm.

Alpha-Beta Pruning is used to reduce unnecessary branches of the search tree and improve the efficiency of the decision-making process.

## AI Approach

### Minimax Search

The agent uses the Minimax algorithm to explore possible future game states.

At each level of the search tree:

- The maximizing player searches for moves that increase the evaluation score.
- The minimizing player searches for moves that decrease it.
- The search continues until the specified depth limit or a terminal state is reached.

The implementation uses a search depth of 3.

### Alpha-Beta Pruning

Alpha-Beta Pruning is incorporated into Minimax to avoid exploring branches that cannot affect the final decision.

This reduces the number of game states that need to be evaluated while preserving the result of the Minimax search.

### Heuristic Evaluation

Since exploring the entire Connect Four game tree is computationally expensive, the agent uses a heuristic function to estimate the quality of non-terminal board states.

The evaluation considers patterns such as:

- Winning four-piece sequences
- Three connected pieces with an available space
- Two connected pieces with available spaces
- Opponent threats
- Horizontal patterns
- Vertical patterns
- Diagonal patterns
- Control of the center column

The heuristic assigns different scores to these patterns to estimate how favorable a board state is for the AI player.

### Move Ordering

Candidate moves are considered using a center-first ordering:

```text
[3, 2, 4, 1, 5, 0, 6]
```

In Connect Four, central positions generally participate in more possible winning combinations. Considering these moves earlier can also help Alpha-Beta Pruning eliminate branches more effectively.

## Decision-Making Process

The overall decision process of the agent can be summarized as:

```text
Receive Opponent Move
        |
        v
Update Internal Board
        |
        v
Find Valid Columns
        |
        v
Generate Candidate Moves
        |
        v
Minimax Search
        |
        v
Alpha-Beta Pruning
        |
        v
Heuristic Evaluation
        |
        v
Select Best Move
        |
        v
Send AI Move
```

## Board Representation

The game board is represented internally as a 6 × 7 matrix.

Each cell represents one of three possible states:

- Empty position
- AI piece
- Opponent piece

The board representation is updated as new moves are received during the game.

## Game Platform Integration

The AI component was designed to interact with an existing game platform.

The notebook includes communication with the platform through:

- REST API requests
- WebSocket communication

This allows the agent to receive game information and submit its selected moves.

The external game platform itself is not included in this repository.

## Repository Contents

```text
.
├── human_vs_bot.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

The Jupyter Notebook contains the original implementation developed for the course project.

## Running the Notebook

1. Clone the repository:

```bash
git clone <repository-url>
cd <repository-name>
```

2. Install the required Python packages:

```bash
pip install -r requirements.txt
```

3. Start Jupyter Notebook:

```bash
jupyter notebook
```

4. Open `human_vs_bot.ipynb` and run the cells in order.

> **Note:** Parts of the notebook communicate with the original external game platform. These sections may not function independently if that platform or its services are no longer available. The AI implementation itself remains available in the notebook for inspection.

## Technologies and Concepts

- Python
- Jupyter Notebook
- Artificial Intelligence
- Minimax Algorithm
- Alpha-Beta Pruning
- Heuristic Search
- Game Tree Search
- REST API
- WebSocket Communication

## Academic Context

This project was developed as part of an undergraduate Artificial Intelligence course.

The main objective of my contribution was to apply classical AI search techniques to a practical game-playing problem, including game-state representation, heuristic design, Minimax search, and Alpha-Beta Pruning.

## Author

**Yalda Mousavi**

Computer Engineering Student  
Interested in Machine Learning, Artificial Intelligence, and Backend Development