# TSP Problem — Evolutionary Algorithm

A Python implementation of several Evolutionary Algorithm (EA) configurations to solve the **Travelling Salesman Problem (TSP)** on a 127-city dataset.

## Problem Description

The Travelling Salesman Problem asks: given a list of cities and the distances between them, what is the shortest possible route that visits every city exactly once and returns to the starting city?

This project explores 8 different EA configurations and compares their performance on a benchmark dataset of 127 cities (`TSPDATA.txt`).

## Algorithm Components

Each EA configuration combines one choice from each of the three stages below.

### Parent Selection
| Method | Description |
|--------|-------------|
| **Linear Ranking** | Assigns selection probabilities based on rank order (pressure parameter `s = 1.5`) |
| **FPS** (Fitness Proportionate Selection) | Assigns selection probability proportional to fitness value |

Both methods use **Roulette Wheel** sampling to pick parents.

### Crossover
| Method | Description |
|--------|-------------|
| **PMX** (Partially Mapped Crossover) | Copies a random segment from one parent and fills the rest using position mappings from the other parent |
| **Edge Recombination Crossover** | Builds offspring by following edges that appear in either parent, preferring edges shared by both |

### Mutation
| Method | Description |
|--------|-------------|
| **Swap Mutation** | Randomly selects two positions and swaps their city values |
| **Insert Mutation** | Removes a city from a random position and re-inserts it at another random position |

## EA Configurations

| # | Parent Selection | Crossover | Mutation |
|---|-----------------|-----------|----------|
| EA 1 | Linear Ranking | PMX | Swap |
| EA 2 | Linear Ranking | PMX | Insert |
| EA 3 | Linear Ranking | Edge | Swap |
| EA 4 | Linear Ranking | Edge | Insert |
| EA 5 | FPS | PMX | Swap |
| EA 6 | FPS | PMX | Insert |
| EA 7 | FPS | Edge | Insert |
| EA 8 | FPS | Edge | Swap |

## Parameters

| Parameter | Value |
|-----------|-------|
| Population Size | 100 |
| Generations | 1000 |
| Mutation Rate | 0.1 |

## Fitness Function

Fitness is defined as the inverse of the total tour distance:

```
fitness = 1 / total_tour_distance
```

A higher fitness corresponds to a shorter (better) route.

## Dataset

`TSPDATA.txt` contains the coordinates of **127 cities** in the format:

```
DIMENSION : 127
NODE    X      Y
   1   9860  14152
   2   9396  14616
   ...
```

## Requirements

- Python 3.x
- [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)
- [Jupyter Notebook](https://jupyter.org/)

Install dependencies:

```bash
pip install numpy matplotlib notebook
```

## Usage

Open and run the Jupyter Notebook:

```bash
jupyter notebook EC-Assignment1.ipynb
```

Each section of the notebook corresponds to one EA configuration. After running all generations, the notebook plots the best tour distance per generation and displays the best route found.

## Project Structure

```
.
├── EC-Assignment1.ipynb   # Main notebook with all 8 EA implementations
├── EC-Assignment1.pdf     # Report / assignment write-up
├── Problem-Phase.pdf      # Problem statement
├── TSPDATA.txt            # 127-city TSP dataset
└── README.md
```
