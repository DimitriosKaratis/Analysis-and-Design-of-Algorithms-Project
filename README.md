# Analysis and Design of Algorithms Project

This repository contains the implementation of three projects in **Analysis and Design of Algorithms**, demonstrating practical applications of theoretical computer science concepts to real-world optimization problems, emphasizing both in algorithmic efficiency and mathematical rigor.  
The work was developed as part of the *Analysis and Design of Algorithms* course at the **Department of Electrical and Computer Engineering, Aristotle University of Thessaloniki.**

---

## 📌 Projects Overview

This project presents solutions to three algorithmic problems focusing on graph algorithms, greedy algorithms, and dynamic programming. Each problem required designing efficient algorithms, providing mathematical proofs of correctness, and analyzing time complexity.

## Project Structure

- **LaTeX Source**: Complete academic report with mathematical proofs and algorithm analysis
- **Problem Solutions**: Three distinct algorithmic challenges with detailed solutions
- **Pseudocode**: Formal algorithm implementations for each solution
- **Complexity Analysis**: Rigorous time complexity evaluations

## Problem Descriptions and Solutions

### 🔹 Problem 1: Graph Connectivity with Fuel Constraints

**Task**: Design algorithms to determine if travel between cities is feasible given fuel tank limitations.

#### Question 1: Route Existence
**Problem**: Given a graph of cities connected by roads with specific lengths, determine if there exists a feasible route from city `s` to city `t` with a fuel tank capacity `L`.

**Approach**:
- **Graph Preprocessing**: Remove all edges (roads) with length > L before applying search algorithms
- **Algorithm**: Modified Breadth-First Search (BFS) on the filtered graph
- **Logic**: If city `t` remains unvisited (white) after BFS completion, no feasible route exists

**Key Insights**:
- Simplification through edge filtering reduces problem complexity
- BFS naturally explores all reachable vertices within fuel constraints
- **Time Complexity**: O(|V| + |E|) - same as standard BFS

#### Question 2: Minimum Tank Capacity
**Problem**: Find the minimum fuel tank capacity required to travel from city `s` to city `t`.

**Approach**:
- **Preliminary Check**: Use Dijkstra's algorithm to verify connectivity
- **Core Algorithm**: Modified Prim's MST algorithm focusing on bottleneck edges
- **Strategy**: Track maximum edge weight in the MST path from `s` to `t`

**Key Insights**:
- Problem reduces to finding the bottleneck edge in the optimal path
- MST properties ensure minimal maximum edge weight
- Greedy selection of minimum edges leads to optimal solution
- **Time Complexity**: O((|V| + |E|)log|V|) using binary heap

### 🔹 Problem 2: Citizen Service Queue Optimization

**Task**: Minimize total waiting time for citizens requiring government services.

**Problem**: Given `n` citizens with different service times, determine the optimal service order to minimize total waiting time across all citizens.

**Approach**:
- **Strategy**: Shortest Processing Time First (SPT) - serve citizens in ascending order of service time
- **Algorithm**: Sort citizens by service time, then process in order
- **Proof Method**: Proof by contradiction showing any deviation increases total cost

**Mathematical Proof**:
- Demonstrated that swapping any two citizens in non-optimal order increases total waiting time
- For citizens with service times `t_i < t_{i+1}`, serving `t_i` first saves `(t_{i+1} - t_i)` units of total waiting time
- Proved optimality through adjacent swap analysis

**Key Insights**:
- Greedy approach yields globally optimal solution
- Each local optimization (shortest job first) contributes to global minimum
- **Time Complexity**: Dominated by sorting - O(n log n) using mergesort

### 🔹 Problem 3: Optimal String Segmentation

**Task**: Find minimum computational cost to cut a string into specified segments.

**Problem**: Given a string of length `n` and `m` required cut positions, determine the minimum cost sequence of cuts where each cut costs the length of the current segment being cut.

**Approach**:
- **Technique**: Dynamic Programming with optimal substructure
- **State Definition**: `C[i,j]` = minimum cost to make all required cuts between positions `P[i]` and `P[j]`
- **Recurrence**: `C[i,j] = min{P[j] - P[i] + C[i,k] + C[k,j]}` for all valid cut positions `k`

**Algorithm Design**:
- Extended cut position array to include boundaries (0 and n)
- Bottom-up computation filling cost matrix diagonally
- Base cases: adjacent positions have zero cost (no cuts possible)

**Key Insights**:
- Problem exhibits optimal substructure: optimal solution contains optimal solutions to subproblems
- Order of cuts affects total cost due to changing segment lengths
- Dynamic programming captures all possible cut sequences efficiently
- **Time Complexity**: O(m³) - similar to matrix chain multiplication

## Technical Implementation

### Algorithm Characteristics

**Problem 1**: 
- Graph algorithms with preprocessing optimization
- BFS modification for constraint handling
- MST application for bottleneck optimization

**Problem 2**:
- Greedy algorithm with mathematical optimality proof
- Exchange argument demonstration
- Priority queue implementation for efficiency

**Problem 3**:
- Dynamic programming with interval-based subproblems
- Optimal substructure exploitation
- Bottom-up computation strategy

### Complexity Summary

| Problem | Algorithm Type | Time Complexity | Space Complexity |
|---------|----------------|-----------------|------------------|
| 1.1 | Modified BFS | O(\|V\| + \|E\|) | O(\|V\|) |
| 1.2 | Modified Prim's | O((\|V\| + \|E\|)log\|V\|) | O(\|V\|) |
| 2.1 | Greedy (SPT) | O(n log n) | O(n) |
| 3.1 | Dynamic Programming | O(m³) | O(m²) |

## Mathematical Rigor

The project demonstrates several proof techniques:

1. **Correctness Proofs**: Formal arguments for algorithm correctness
2. **Optimality Proofs**: Mathematical demonstration of optimal solutions
3. **Complexity Analysis**: Rigorous time and space complexity evaluation
4. **Contradiction Arguments**: Proof by contradiction for greedy algorithm optimality

## Implementation  
- Report is written in Greek, while the README provides an English overview.  
