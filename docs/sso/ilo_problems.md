# (Integer) Linear Optimization Problems

## General setup


1. Define decision variables
2. Define objective
3. Define restrictions/constraints
4. Solve (graphically or algebraically)


## Product mix
**Decision variables**   
$x_i$: quantitiy of product $i$ produced for $i=1,2,...n$

**Objective**  
maximize profit $max \sum_{i=1}^n p_i x_i$

**Constraints**

- product unit constraints
- $x_i \geq 0$

## Project planning
**Decision variables**  
$x_i$ start time of activity $i$ $\forall_i$

**Objective**  
minimize project finish time $min max (x_i + d_i)$ for $d_i =$ duration of $i$

but non linear, therefore:  
$min z$

**Constraints**  
$z \geq x_i + d_i$

$x_i + d_i \leq x_j$

$x_i \geq 0$

<img src="/img/project_start.png" alt="trans">

## ILO (Branch & bound)


## Transportation problem
<img src="/img/transportation.png" alt="trans">


## Set covering problem
**Objective**  
Minimize number of sets taken

<img src="/img/set_covering.png" alt="trans">

## Shift scheduling
<img src="/img/shift_scheduling.png" alt="trans">

## Machine scheduling
<img src="/img/machine_scheduling_1.png" alt="trans">
<img src="/img/machine_scheduling_2.png" alt="trans">

## Multi-period inventory problem
<img src="/img/inventory.png" alt="trans">

## Shortest-path problem
<img src="/img/shortest_path.png" alt="trans">

## Maximum flow
<img src="/img/maximum_flow.png" alt="trans">


## Absolute values trick






