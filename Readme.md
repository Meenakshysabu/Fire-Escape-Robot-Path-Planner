#### 🔥 Fire Escape Robot Path Planner

An intelligent **Fire Escape Robot Path Planner** that simulates a robot navigating through a building while avoiding dynamically spreading fire and finding a safe route to an exit.

The project combines **A* pathfinding, dynamic fire simulation, heat-aware navigation, and a Tkinter-based visual interface** to demonstrate how an autonomous robot can make escape decisions in a dangerous environment.

### 🚀 Features

 #🤖Autonomous Robot Navigation

  * Simulates a robot moving through a building.
  * Finds routes from the starting position to available exits.

 #🔥Dynamic Fire Simulation

  * Fire spreads across the building over time.
  * Fire spread is probabilistic and changes the environment dynamically.
  * Fire can spread through neighboring cells and create complex scenarios.

#🧠 Heat-Aware A* Pathfinding

  * Uses the A* algorithm to find efficient paths.
  * Considers fire and heat when selecting a route.
  * Avoids dangerous cells whenever possible.

#🛡️ Fire Avoidance

  * Checks whether the next robot position is safe.
  * Considers nearby fire when evaluating paths.
  * Can switch to alternative routes when the current path becomes unsafe.

#🚪Multiple Exit Selection

  * Supports multiple exits in the building.
  * Can select an exit based on distance and safety.

#🆘Emergency Escape

  * If a normal safe route cannot be found, the planner attempts an emergency escape route.
  * Can allow high-cost fire cells as a last-resort strategy.

#🖥️ Interactive GUI

  * Built using Tkinter.
  * Visualizes the building, robot, fire, exits, and movement.
  * Includes Play, Pause, Reset, and Next controls.

## 🧩 Technologies Used

* Python
* NumPy
* Tkinter
* Pillow (PIL)
* OpenCV
* Matplotlib
* MSS
* A* Pathfinding Algorithm

### 📁 Project Structure

Fire-Escape-Robot-Path-Planner/
│
├── README.md
├── requirements.txt
│
├── assets/
│   ├── robot.png
│   ├── fire.png
│   └── exit.png
│
├── Map/
│   └── building_map.txt
│
└── src/
    ├── cell_types.py
    ├── fire.py
    ├── grid.py
    ├── heat_aware_astar.py
    ├── heat_aware_astar_improved.py
    ├── planner.py
    └── gui_tkinter_building.py


## 🗺️ Building Map

The building is represented using an ASCII-based map.

| Symbol | Meaning               |
| ------ | --------------------- |
| `.`    | Empty / Walkable cell |
| `#`    | Wall                  |
| `F`    | Fire                  |
| `E`    | Exit                  |
| `S`    | Robot Start           |

Example:


###########################E##################
#.....#.....#.....#.....#.....#.....#.....#..#
#.###.#.###.#.###.#.###.#.###.#.###.#.###.#..#
#.T.#.#.T.#.#.F.#.#.T.#.#.T.#.#.F.#.#.F.#.#S.#
E...#.....#.....#.....#.....#.....#.....#....#


The map is loaded and converted into a numerical grid before the simulation begins.

## 🧠 How It Works

The project works in several stages.

### 1. Load the Building

The ASCII map is read by the `Grid` class and converted into a NumPy array.

The system identifies:

* Robot starting position
* Building walls
* Existing fire
* Available exits

### 2. Calculate Fire Conditions

The `FireSpread` system simulates how fire spreads throughout the building.

Fire spread is controlled using a probability value, making each simulation capable of producing different scenarios.

### 3. Calculate Heat

A heatmap is generated based on the current fire locations.

Cells closer to fire can receive higher costs, encouraging the robot to stay away from dangerous areas.

### 4. Find a Path

The planner uses an **A*** search algorithm to find a route to an exit.

Instead of considering only distance, the planner can also consider:

* Fire cells
* Heat
* Nearby fire
* Path length
* Exit safety

This allows the robot to prefer a slightly longer but safer route.

### 5. Recalculate When Fire Spreads

Because the environment changes dynamically, the robot can recalculate its route when fire blocks or threatens the current path.

### 6. Emergency Escape

If a completely safe path cannot be found, the planner can use an emergency strategy and, as a last resort, allow movement through fire cells with a very high cost.

## 🔍 Pathfinding Algorithm

The main pathfinding technique used is **A***.

The algorithm evaluates each possible position using:

```text
f(n) = g(n) + h(n)
```

Where:

* `g(n)` = cost of reaching the current cell
* `h(n)` = estimated distance to the goal
* `f(n)` = total estimated cost

The project improves normal A* by adding additional costs related to fire and heat.

For example:

```text
Normal cell → Low cost
Hot cell → Higher cost
Near fire → Higher penalty
Fire cell → Very high cost
Wall → Not walkable
```

This encourages the robot to find routes that are both **efficient and safer**.

## 🖥️ GUI Controls

The application provides an interactive simulation interface.

| Button       | Function                          |
| ------------ | --------------------------------- |
| ▶ **PLAY**   | Start the simulation              |
| ⏸ **PAUSE**  | Pause the simulation              |
| 🔄 **RESET** | Reset the building and simulation |
| ⏭ **NEXT**   | Move to the next simulation run   |

The interface displays the robot's movement and the changing fire conditions in real time.

## ⚙️ Installation

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/Fire-Escape-Robot-Path-Planner.git
```

### 2. Open the Project

```bash
cd Fire-Escape-Robot-Path-Planner
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

> Tkinter is normally included with Python on Windows. If it is not available on your system, install the appropriate Tk/Tcl package for your operating system.

## ▶️ Run the Project

From the project root directory:

```bash
python -m src.gui_tkinter_building
```

Alternatively, you can run:

```bash
python src/gui_tkinter_building.py
```

depending on your Python package configuration.

## 🎯 Project Objective

The main objective of this project is to demonstrate how **intelligent path planning can be used for autonomous robot navigation in emergency situations**.

The robot must continuously balance:

```text
Shortest Path
      +
Fire Avoidance
      +
Heat Awareness
      +
Exit Safety
      ↓
Safe Escape Route
```

## 🌟 Applications

This concept can be extended to real-world applications such as:

* 🚒 Firefighting robots
* 🏢 Smart building evacuation systems
* 🤖 Autonomous emergency robots
* 🏭 Industrial safety systems
* 🚨 Disaster-response systems
* 🧭 Dynamic obstacle navigation
* 🏥 Emergency evacuation planning
