# Event Log Analysis of Employee Energy

## Overview
This repository contains code to analyze event log data from childcare organizations. The goal is to identify patterns in daily activities associated with low employee energy and to evaluate interventions that may improve overall energy levels.

## Data
The analysis uses survey-based event logs containing:
- Activities (JSON format)  
- Durations and timestamps  
- Self-reported energy levels  
- Anonymized employee IDs

> **Note:** Due to privacy and confidentiality constraints, the survey data is not included in this repository.  
> The dataset may be shared at a later stage in an anonymized or approved form.

## Method

### 1. Event Log Construction
Daily survey responses are transformed into structured event logs:
- Each day is treated as a **trace**
- Activities are ordered and timestamped
- Duration and energy levels are preserved

### 2. Pattern Detection
Six energy-related patterns are identified:

- **P1: Low energy levels**  
  Frequently occurring activities with low average energy.

- **P2: Variation in energy**  
  Activities where energy levels differ strongly between employees.

- **P3: Time-of-day effects**  
  Activities with different energy levels in the morning vs. afternoon.

- **P4: Start-of-day trap**  
  Short activities early in the day associated with low energy.

- **P5: Long energy-draining tasks**  
  Long-duration activities with consistently low energy.

- **P6: Repeated low-energy tasks**  
  Activities performed multiple times per day with low energy.

For each pattern, severity scores are computed and normalized, and the **top 3 activities** per pattern are selected.

### 3. Intervention Simulation
For each pattern, targeted interventions are simulated, such as:
- Removing or reducing low-energy activities  
- Reassigning tasks between employees  
- Eliminating low-energy time segments  
- Splitting long tasks with breaks  
- Merging repeated activities  

Impact is measured using:
- **ΔEnergy** (change in mean energy)  
- **% improvement**

## Results
Estimated energy improvements range from **0% to 27%**, depending on the pattern and dataset.

## Usage
1. Install dependencies:
```bash
pip install -r requirements.txt
```
2. Place data in the folder named `survey data/`

3. Run the notebook:
```bash
jupyter notebook "Pattern analysis/Analysis.ipynb"
