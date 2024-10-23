# README

## Overview

This repository contains two Python scripts designed to model and analyze the dynamics of susceptible, infected, free-living parasitic, and refuge populations using ordinary differential equations.

## Files

- `script1_modelcode.py`
- `script2_parametervariation.py`

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

This script simulates the dynamics of the populations with a specific set of parameters and initial conditions. It computes and plots the time course of the populations of susceptible individuals (S), infected individuals (I), parasites (P), and individuals in refuge (R).

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

This script explores the impact of varying the `muin` and `muout` parameters on the population dynamics. It creates a mesh grid of `muin` and `muout` values and calculates the maximum range of parasite population (P) fluctuations to identify parameter combinations that lead to population cycling.

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

#### Initial Conditions

- `N0 = (np.log(10), np.log(10), np.log(10), np.log(1))`: Logarithmic scale initial conditions for the populations.

#### Time Points

- `tc = np.linspace(100, 500, 5001)`: Time points for the simulation.

#### Model

The model function calculates the rates of change for each population based on the provided parameters and current population sizes.

#### Output

- A contour plot showing the impact of `muin` and `muout` on the cycling behavior of the parasite population.
