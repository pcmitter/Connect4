# 🎮 Connect 4: Human vs AI

An interactive **Connect 4 game built using Python, Jupyter Notebook, HTML, CSS, and JavaScript**, featuring a human-versus-AI gameplay experience, multiple difficulty levels, score tracking, and visual win detection.

The project combines a Python-based game engine and a PyTorch neural network architecture with a custom HTML/CSS/JavaScript interface rendered directly inside a Jupyter Notebook.

## ✨ Features

- **Human vs AI Gameplay:** Play Connect 4 against a computer opponent.
- **Three Difficulty Levels:**
  - 🟢 **Easy:** Primarily random moves with a small chance of blocking an immediate winning move.
  - 🟡 **Medium:** Prioritizes winning moves, blocks immediate human wins, and otherwise selects a random move.
  - 🔴 **Expert:** Checks immediate winning and blocking opportunities, then prioritizes the center columns.
- **Interactive Game Board:** Click any column to drop your disc.
- **Live Scoreboard:** Tracks human wins, AI wins, and draws across consecutive rounds.
- **Winning Line Animation:** Highlights the winning combination with a green line.
- **New Game Option:** Reset the board without restarting the notebook.
- **Custom Dark-Themed UI:** A visually styled game interface with red human discs and yellow AI discs.
- **Neural Network Architecture:** Includes a PyTorch-based value network designed to map board states to a scalar evaluation.
- **Notebook-Based Execution:** The game interface is displayed directly inside Jupyter Notebook using `IPython.display.HTML`.

## 🖥️ Game Overview

The game uses the standard Connect 4 board, consisting of **6 rows and 7 columns**. Players take turns dropping discs into columns, and the first player to connect four discs horizontally, vertically, or diagonally wins.

| Component | Description |
|---|---|
| Game board | 6 × 7 grid |
| Human player | Red discs |
| AI opponent | Yellow discs |
| Winning condition | Four consecutive discs |
| Difficulty modes | Easy, Medium, Expert |
| Interface | Interactive HTML/CSS/JavaScript |
| Execution environment | Jupyter Notebook |

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Game engine and notebook execution |
| NumPy | Board representation and numerical operations |
| PyTorch | Neural network architecture |
| HTML | Game interface structure |
| CSS | Board styling and visual presentation |
| JavaScript | User interaction, AI move selection, and win detection |
| IPython | Rendering the interactive HTML interface inside the notebook |
| Jupyter Notebook | Development and execution environment |

## 📂 Project Structure

```text
Connect4-Game/
│
├── Connect4.ipynb     # Main notebook containing the game
└── README.md          # Project documentation
```

*Replace `Connect4.ipynb` with your actual notebook filename if it differs.*

## 🚀 Getting Started

### 1. Clone the Repository

Open a terminal and run:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

Replace `YOUR-USERNAME` and `YOUR-REPOSITORY` with your GitHub username and repository name.

### 2. Navigate to the Project Directory

```bash
cd YOUR-REPOSITORY
```

### 3. Install the Required Libraries

Make sure Python is installed, then run:

```bash
pip install numpy torch jupyter ipython
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open the Connect 4 notebook from the Jupyter interface.

### 5. Run the Game

Execute the notebook cells in order, from the library imports through the cell that displays the HTML interface.

Once the interface appears, select a difficulty level and click any column to make your move.

**Note:** The interactive interface relies on JavaScript execution in the notebook's HTML output. For the intended gameplay experience, run the notebook in a compatible Jupyter environment rather than viewing it only through GitHub's static notebook preview.

## 🎯 How to Play

1. Launch the notebook and execute all required cells.
2. Select Easy, Medium, or Expert difficulty.
3. Click a column on the board to drop your red disc.
4. Wait for the AI to make its yellow-disc move.
5. Connect four of your discs horizontally, vertically, or diagonally to win.
6. Check the scoreboard to track wins and draws.
7. Click **New Game** to start another round.

## 🧠 AI Decision-Making

The opponent uses a rule-based decision-making strategy that varies with the selected difficulty.

### Easy Mode

- Checks for potential human winning moves.
- Has a 20% chance of choosing an immediate blocking move when one is available.
- Otherwise, selects a valid column randomly.

### Medium Mode

- Checks whether the AI can win immediately.
- Blocks an immediate human winning move if necessary.
- Selects a random valid column when neither condition applies.

### Expert Mode

- Prioritizes an immediate AI winning move.
- Blocks an immediate human winning move.
- Prefers the center column, followed by adjacent columns, when no immediate win or block is available.

The Expert mode is a heuristic-based opponent, not a complete game-tree-search AI. It does not guarantee optimal play against every possible board position.

## 🧮 Neural Network Architecture

The notebook also defines a feed-forward neural network named `Connect4ValNet` using PyTorch.

Its architecture is:

```text
Input Board State (6 × 7 = 42 values)
                 │
                 ▼
          Fully Connected
              42 → 128
                 │
               ReLU
                 │
                 ▼
          Fully Connected
              128 → 64
                 │
               ReLU
                 │
                 ▼
          Fully Connected
               64 → 1
                 │
               Tanh
                 │
                 ▼
        Scalar Board Evaluation
```

The network maps a flattened board representation of 42 values to a single output constrained by the `Tanh` activation function.

**Implementation note:** The current notebook initializes this neural network but does not train it or use its predictions to select AI moves. Actual gameplay decisions are made by the JavaScript heuristic logic described above. The network provides a foundation for future machine-learning-based AI development.

## 🔍 Core Game Logic

The Python game engine defines the board and basic operations:

- `reset()` — Initializes an empty board.
- `is_valid_col(col)` — Checks whether a column has space available.
- `get_open_row(col)` — Finds the lowest available row in a column.

The JavaScript interface implements the interactive gameplay:

- `userClick(col)` — Processes a human move.
- `aiMove()` — Executes the AI's move.
- `chooseCol()` — Selects a move according to the chosen difficulty.
- `checkWin(player)` — Checks horizontal, vertical, and diagonal winning combinations.
- `isFull()` — Detects a full board.
- `resetBoard()` — Starts a new round.
- `drawWinStrike(coords)` — Draws a line across the winning combination.

## 🔮 Future Improvements

Potential extensions include:

- Training the neural network on Connect 4 board positions.
- Integrating the trained network into AI move selection.
- Implementing the Minimax algorithm with alpha-beta pruning.
- Adding move previews and disc-drop animations.
- Improving mobile responsiveness and accessibility.
- Saving match history and statistics between notebook sessions.
- Adding player-versus-player gameplay.
- Comparing heuristic AI performance with trained neural network and search-based agents.

## 📚 Learning Outcomes

This project demonstrates practical concepts in:

- Object-oriented programming.
- Two-dimensional board representations using NumPy.
- Artificial intelligence and heuristic-based decision-making.
- Neural network architecture using PyTorch.
- HTML, CSS, and JavaScript integration.
- Interactive visualization in Jupyter Notebook.
- Game-state management and win-condition detection.

## 👨‍💻 Author

**Palash Chowdhury**
