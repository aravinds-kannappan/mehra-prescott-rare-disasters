# Mehra-Prescott Rare Disasters Model Extension

## Overview
This repository contains code and data for extending the Mehra-Prescott (1985) model to address the equity premium puzzle by incorporating rare economic disasters. The project introduces a disaster state with state-dependent probabilities, persistence, and an updated empirical calibration reflecting U.S. data from the Great Recession (2007–2009) and COVID-19 pandemic (2020). The model evaluates impacts on risk-free rates, risk premia, and state-dependent yield curves using empirical and Generalized Method of Moments (GMM) calibration techniques.

---

## Key Objectives
- Extend the Mehra-Prescott model with a three-state Markov chain to include normal growth, low growth, and disaster states.
- Analyze how disaster probability, severity, and persistence affect asset pricing metrics.
- Calibrate the model using historical U.S. data, including recent economic downturns.
- Compare empirical and GMM calibration methods to assess their effectiveness in resolving the equity premium puzzle.

---

## Mathematical Concepts

### Equity Premium Puzzle
The observed high equity risk premium (5–7% historically) and low risk-free rate cannot be explained by standard consumption-based models with reasonable risk aversion levels.

### Three-State Markov Chain
Models consumption growth with states: high growth, low growth, and disaster. Transition probabilities govern state switches, with disaster probabilities `d₁` (from high growth) and `d₂` (from low growth), and persistence `p`.

### Risk-Free Rate
Derived from the inverse of the expected marginal utility of consumption, adjusted for disaster risk—lowered due to precautionary savings.

### Risk Premium
The difference between expected equity returns and the risk-free rate, elevated by rare disasters due to higher perceived risk.

### State-Dependent Yield Curves
Interest rates vary by state, with higher short-maturity rates in low-growth and disaster states due to increased uncertainty.

### GMM Calibration
Estimates parameters (`d₁`, `d₂`, `p`, and others) by minimizing moment conditions, capturing asymmetry in disaster probabilities and persistence.

---

## Techniques Used

### Empirical Calibration
- Uses historical U.S. GDP data (FRED, Maddison 2003) to estimate disaster parameters.
- Defines disasters as a 5%+ drop in real per capita GDP.
- Identifies the Great Depression (31% drop, 1929–1933), Great Recession (5.1% drop, 2007–2009), and COVID-19 (9.3% drop, 2019–2020).
- Parameters:
  - `μ = 0.018` (mean consumption growth)
  - `σ = 0.036` (volatility)
  - `γ = 0.43` (risk aversion)

### GMM Calibration
- Estimates disaster parameters using four moment conditions to match empirical moments (e.g., average equity return).
- Captures asymmetry (`d₂ > d₁`) and persistence (`p > 0`), but struggles with realistic risk premia (5–7%) and occasionally produces negative risk-free rates.

### Simulation and Visualization
- Generates plots:
  - **Figure 1**: Model with/without disaster state  
  - **Figure 2**: Effect of lower disaster probability  
  - **Figure 3**: Effect of disaster severity  
  - **Figure 5**: Yield curves

---

## Requirements

- Python 3.8+
- Libraries:
  - NumPy
  - Pandas
  - SciPy
  - Matplotlib

### Data:
- U.S. real per capita GDP (`FRED: A794RXQ0048SBEA`)
- Personal Consumption Expenditures (`PCECTPI`)
- Kenneth French’s asset returns dataset

---

## Installation

```bash
git clone https://github.com/sophiacho1/mehra-pescottrare-disasters.git
cd mehra-pescottrare-disasters
pip install -r requirements.txt
```

---

## Usage

```bash
# Run empirical calibration
python empirical_calibration.py

# Run GMM calibration
python gmm_calibration.py
```

### Outputs:
- **Plots**: Risk-free rates, risk premia, and yield curves (`figures/`)
- **Tables**: GMM results and model comparisons (e.g., Table 1, Table 2)

---

## Files

- `empirical_calibration.py`: Implements empirical calibration using historical GDP and consumption data.
- `gmm_calibration.py`: Performs GMM calibration for disaster parameters.
- `data/`: Contains FRED GDP data, PCECTPI, and Kenneth French’s asset returns.
- `figures/`: Stores generated plots.
- `requirements.txt`: Lists required Python libraries.

---

## Key Findings

- Rare disasters lower average risk-free rates and raise risk premia, improving model fit to U.S. data.
- Higher disaster probability or severity enhances the model’s ability to explain the equity premium puzzle.
- Disaster persistence has ambiguous effects, requiring further study.
- GMM calibration captures asymmetric disaster probabilities but fails to produce realistic risk premia, indicating potential misspecification.

---

## Future Directions

- Incorporate aggregate dividends instead of consumption growth.
- Refine GMM calibration to address misspecification.
- Explore alternative risk preferences (e.g., Epstein-Zin, habit formation).
- Model state-dependent disaster severities (Gabaix, 2012).
- Extend to international markets (Nakamura et al., 2013).

---

## Acknowledgments

- Jaroslav Borovička and Hyein Han for invaluable guidance.  
- Data sources: FRED, Kenneth French’s website, Maddison (2003).

---

## License

MIT License

