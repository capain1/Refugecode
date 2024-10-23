# README

## Overview

This repository contains two Python scripts designed to model and analyze the dynamics of susceptible, infected, free-living parasitic, and refuge populations using ordinary differential equations.

## Files

- `script1_modelcode.py`
- `script2_parametervariation.py`
- `script3_prevalence.ipynb`

## Requirements

- Python 3.x
- `numpy`
- `scipy`
- `matplotlib`

Install the necessary packages using:

```bash
pip install numpy scipy matplotlib
```

## Usage

1. Clone the repository:

```bash
git clone https://github.com/capain1/Refugecode.git
cd Refugecode
```

2. Run the scripts using Python:

```bash
python script1.py
python script2.py
```

## Script Descriptions

### Script 1: Model code, default parameter

#### Description
This script models the Susceptible-Infected (SI) dynamics of a population with a free-living parasite stage and a refuge for susceptible individuals. It solves a system of differential equations with default parameter values to simulate how susceptibles (S), infected individuals (I), parasites (P), and refuge population (R) evolve over time. The model calculates population dynamics under specific conditions such as growth rates, infection rates, and movement between the population and refuge.

The key feature of this script is its use of log-transformed initial conditions, allowing it to handle a wide range of population sizes efficiently. The model then transforms the output back to its original scale for interpretation. The results are plotted to visualize how each population fluctuates over time.

##### Key steps:
- Solving the system: The script uses scipy.integrate.solve_ivp to solve the system of differential equations, tracking the evolution of S, I, P, and R over the specified time points.
- The script outputs maximum values for each state variable, representing the peak population sizes for each category.
- Visualization: It generates a plot showing the time course of each population: susceptibles, infected, parasites, and the refuge population, demonstrating how they change over time.

#### Parameters

- `r = 2`: Growth rate of the susceptible population.
- `c = 1`: Normal death rate.
- `beta = 0.1`: Infection rate (increased from 0.02 to 0.1).
- `gamma = 0.1`: Extra death rate from infection.
- `b = 0.3`: Death rate of parasites.
- `n = 5`: Burst size (growth rate of the parasite).
- `k = 1000`: Carrying capacity of the susceptible population.
- `muout = 4`: Rate at which susceptibles enter the population from refuge.
- `muin = 1`: Rate at which susceptibles leave the population into refuge.
- `alpha = 0.3`: Death rate in refuge.
- `m = 1000`: Carrying capacity of the refuge population.
- `f = 0`: Fecundity

#### Initial Conditions

- `N0 = (np.log(10), np.log(10), np.log(10), np.log(1))`: Logarithmic scale initial conditions for the populations.

#### Time Points

- `tc = np.linspace(0, 500, 5001)`: Time points for the simulation.

#### Model

The model function calculates the rates of change for each population based on the provided parameters and current population sizes.

#### Output

- Maximum values of each state variable over time.
- Plot of the time course of the populations (S, I, P, R).

### Script 2: Parameter variation Analysis

#### Description

This script models the cycling dynamics of a population with a free-living parasite stage and a refuge for susceptible individuals, exploring how varying μin (movement into the refuge) and μout (movement out of the refuge) affects the cycling amplitude. The model tracks log-transformed populations of susceptibles (S), infected individuals (I), free-living parasites (P), and refuge individuals (R).

##### Key steps:
- A mesh grid of muin and muout values is generated to explore different parameter combinations.
- For each combination, the model calculates the cycling amplitude of the parasite population by measuring the difference between the maximum and minimum parasite values over a set time window.
- The results are visualized as a contour plot (heatmap) to show how various values of μin and μout impact cycling amplitude.
- Relative amplitudes are calculated by normalizing the results to a default scenario for easy comparison.

#### Parameters

- `r = 2`: Growth rate of the susceptible population.
- `c = 1`: Normal death rate.
- `beta = 0.02`: Infection rate.
- `gamma = 0.1`: Extra death rate from infection.
- `b = 0.3`: Death rate of parasites.
- `n = 5`: Burst size (growth rate of the parasite).
- `k = 1000`: Carrying capacity of the susceptible population.
- `muout_range = np.arange(0, 10.1, 0.1)`: Range of `muout` values.
- `muin_range = np.arange(0, 10.1, 0.1)`: Range of `muin` values.
- `alpha = 0.3`: Death rate in refuge.
- `m = 1000`: Carrying capacity of the refuge population.
- `f = 0`: Fecundity

#### Initial Conditions

- `N0 = (np.log(10), np.log(10), np.log(10), np.log(1))`: Logarithmic scale initial conditions for the populations.

#### Time Points

- `tc = np.linspace(100, 500, 5001)`: Time points for the simulation.

#### Model

The model function calculates the rates of change for each population based on the provided parameters and current population sizes.

#### Output

- A contour plot showing the impact of `muin` and `muout` on the cycling behavior of the parasite population.

### Script 3: Disease Prevalence Analysis

#### Description

This script explores the prevalence of the infected population in a system with a free-living parasite stage and a refuge for susceptible individuals. The model tracks log-transformed populations of susceptibles (S), infected individuals (I), free-living parasites (P), and refuge individuals (R) to examine how varying the movement rates μin (into the refuge) and μout (out of the refuge) influences disease prevalence over time.

##### Key steps:
- A mesh grid of muin and muout values is created to explore the effects of different parameter combinations on disease prevalence.
- The model calculates the prevalence of infection using the equation:
Prevalence= I / (S+I)
Where I is the infected population and S is the susceptible population. This calculation is performed at each time point.
The prevalence values are averaged over the entire time period to provide an overall measure of average disease prevalence for each combination of μin and μout.
- The results are stored in a 2D array and can be analyzed or visualized to understand how varying μin and μout affects the spread of infection.

#### Parameters

- `r = 2`: Growth rate of the susceptible population.
- `c = 1`: Normal death rate.
- `beta = 0.02`: Infection rate.
- `gamma = 0.1`: Extra death rate from infection.
- `b = 0.3`: Death rate of parasites.
- `n = 5`: Burst size (growth rate of the parasite).
- `k = 1000`: Carrying capacity of the susceptible population.
- `muout_range = np.arange(0, 10.1, 0.1)`: Range of `muout` values.
- `muin_range = np.arange(0, 10.1, 0.1)`: Range of `muin` values.
- `alpha = 0.3`: Death rate in refuge.
- `m = 1000`: Carrying capacity of the refuge population.
- `f = 0`: Fecundity

#### Initial Conditions

- `N0 = (np.log(10), np.log(10), np.log(10), np.log(1))`: Logarithmic scale initial conditions for the populations.

#### Time Points

- `tc = np.linspace(100, 500, 5001)`: Time points for the simulation.

#### Model

The model function calculates the rates of change for each population based on the provided parameters and current population sizes.

#### Output

-A 2D array where each entry represents the average prevalence of the disease for a specific combination of μin and μout values - as a contour plot.
