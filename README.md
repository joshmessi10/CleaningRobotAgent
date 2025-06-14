# 🤖 Cleaning Robot Simulation (With and Without Memory)

This project simulates a robotic agent navigating a 5×5 grid to collect randomly placed leaf debris. The system is implemented in Python using Jupyter Notebook and `ipywidgets` for interactive visualization. The robot operates under two distinct modes:

- **Without Memory:** The agent cleans the environment without storing visited positions.
- **With Memory:** The agent keeps track of cleaned cells using a memory matrix and adapts its behavior to ensure full coverage.

---

## 🧠 Description

The robot starts with a defined amount of energy and a central starting position. As it navigates the grid, it attempts to remove leaf debris (`🍂`) scattered randomly on the board. It consumes one unit of energy per action (scan or move). The simulation ends when energy is exhausted or all debris is removed.

---

## 🔧 Technologies Used

- **Python 3.9+**
- **Jupyter Notebook**
- **ipywidgets** – for dynamic visual rendering of the grid
- **NumPy** – for efficient matrix management and logic

---

## ⚙️ How It Works

### 💡 General Behavior
- The board is displayed as a grid using HTML tables.
- The robot (🤖) moves in cardinal directions.
- It consumes energy while scanning or moving.
- Each cell may or may not contain a piece of debris (`🍂`).
- The robot removes a leaf if it occupies the same cell.

### 📌 Without Memory Mode
- The robot operates reactively.
- It only checks and cleans the current cell.
- Movement is random, without reference to past states.
- No internal representation of visited or cleaned cells is maintained.

### 📌 With Memory Mode
- The robot maintains a `n × n` memory matrix:
  - `0`: Unvisited or uncertain
  - `1`: Visited and clean
- In addition to scanning the current cell, the robot:
  - Scans its 4 neighboring cells (`escaneoVecino`)
  - Updates its memory based on findings
  - Attempts to follow a logical cleaning path
  - Executes a **deep cleaning column-based strategy** if no debris is found after several steps

---

## 🎮 Controls and Functions

| Function | Description |
|---------|-------------|
| `llenadoAleatorio()` | Randomly places leaf debris (`🍂`) on the grid |
| `escaneo()` | Scans and cleans the current cell |
| `escaneoVecino()` | Scans adjacent cells and updates memory matrix |
| `avanzar()` | Moves the robot one step in the direction of its `angulo` |
| `girar(angulo)` | Changes the robot’s orientation |
| `revisionMemoria()` | Checks whether all cells have been visited or verified |
| `limpieza(agente, escenario)` | Main cleaning loop (while energy and uncleaned cells remain) |

---

## 🖼️ Visualization

The grid is rendered as a dynamic HTML table:

- `🤖`: Cleaning robot
- `🍂`: Leaf debris
- Empty cells: Clean and unoccupied

---

## ⚠️ Simulation Parameters

| Parameter | Value |
|----------|-------|
| Grid Size | `5 × 5` |
| Initial Position | `(2, 2)` |
| Initial Energy | `200` |
| Debris Probability | 50% per cell |
| Emoticons | `🤖` (robot), `🍂` (leaf) |

---

## 📊 Outputs

At the end of the simulation, the following are printed:
- ✅ Total leaves collected
- 🔋 Energy consumed
- 🧼 Whether the robot completed a full cleaning (with memory only)

---

## 👥 Credits

Josh Sebastián López Murcia
