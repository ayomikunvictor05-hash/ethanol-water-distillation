# Ethanol–Water Distillation: VLE Model and McCabe-Thiele Design

A Python project that models vapour–liquid equilibrium (VLE) for ethanol–water at 1 atm and uses the model to size a distillation column.

## What it does
- Calculates the vapour pressure of ethanol and water with the Antoine equation
- Builds an ideal-solution model (Raoult's law) and compares it with experimental data
- Fits Wilson activity coefficients to the data
- Uses the McCabe-Thiele method to estimate the reflux ratio and number of theoretical stages

## Results
| Model | Mean error in vapour composition | Mean error in boiling temperature |
|-------|----------------------------------|-----------------------------------|
| Ideal | 0.118 | 7.45 °C |
| Wilson (fitted) | 0.006 | 0.16 °C |

- Fitted Wilson parameters: L12 = 0.1883, L21 = 0.8597
- Azeotrope: model x = 0.899 at 78.15 °C, data x = 0.894 at 78.15 °C
- Example design (5% ethanol feed, 85% distillate, 0.2% bottoms, saturated liquid feed): minimum reflux ratio 1.85, operating reflux ratio 2.40, 24 theoretical stages with the feed at stage 19

## Data and sources
- Experimental data: Hadrich, B. (2009). Identification of the best model and parameters for T-y-x equilibrium data of ethanol-water mixture.
- Antoine constants: Perry's Chemical Engineers' Handbook (8th edition).

## Files
- `ethanol_water_vle.ipynb`: the notebook, with all outputs
- `ethanol_water_vle_1atm.csv`: the experimental data used

## How to run
Install the libraries with `pip install numpy pandas matplotlib scipy jupyter`. Keep the CSV in the same folder as the notebook, open the notebook in Jupyter, and use Kernel → Restart & Run All.

## Limitations
- The model was fitted and checked on the same 15 data points and not tested on a separate data set
- Valid near 1 atm only; the data has no points between the azeotrope and pure ethanol
- McCabe-Thiele assumes constant molar overflow; real columns need more trays than theoretical stages
