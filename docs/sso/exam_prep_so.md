# Exam prep SO

## Learning stuff

### Solvers

- Open source: Cbc
- commercial: best Gurobi, IBM, Cplex


### Modelling languages
There are several: AMPL, AIMMS, GAMS, LINDO, MPL

**Advantages:** quick to model, separation of model and data, different solvers possible, some have IDE, reports

**Disadvantages:** can be expensive, inflexible with other software, learning curve

**PULP**

Advantages:

- open-source
- interface between data, ILO model, solvers (Cbc)
- same as AML + Python

### Complexity stuff

Two classes:

- $p$: exact algorithms that find optimal solutions and run in *polynomial time*, e.g. transportation, shortest path, product mixt problem, LO
- $np$: no exact fast algorithms, heuristics, run in *exponential time* (or larger), e.g. knapsack, machine scheduling, set cover, TSP, ILO

Two ways foward: 

- find the fastest exact algorithm for solving NP-complete problem
- prove that no fastest algorithm for problem exists

Heuristics: 

- metaheuristics: not problem specific (e.g. local search)
- problem specific

**TSP 2-opt**

- find initial route
- remove 1 by 1 all couples of tour edges
- reconnect for valid edges
- repeat until no improvement

### Simulation

**Flaw of averages**: $E[r(X)] \neq r(E[X])$    

**ITM (inverse tranformation method)**

- sample from $unif[0,1]$, using a RNG (random number generator)
- use $F^{-1}(u) = CDF^{-1}(u)$

**Discrete event simulation**  
Simulation of real life process too complex for a function $r(X)$

- discrete sequence of events overt time
- keeps track of state, updates state at each event


**Known inverse CDFs**:

- exponential: $-\log(1-u)/\lambda$
- uniform: $1-U$


**Sidak correction**  
$1 - \sqrt[\vert S \vert - 1]{1 - \alpha}$


## Other stuff
