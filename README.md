# alpha-decay-detection-system

## Overview
Markets evolve, hedge funds may copy your strategy, market microstructure may change, or the macroeconomic regime may shift. As a result, trading signals inevitably lose their edge, a phenomenon known as Alpha Decay. 

This repository contains a Jupyter Notebook built to detect the decay of Alpha. The system treats a trading signal like a biological organism or a radioactive isotope to answer one critical question: *Has my trading signal stopped working?*

## Key Features
1. **Regime Shift Detection:** Identifies structural breaks where monthly alpha shifts from a positive mean (working signal) to near zero (dead signal).
2. **Alpha Half-Life Estimation:** Employs survival analysis to calculate the expected remaining lifespan of a strategy.
3. **Survival Probability Output:** Computes a composite probability determining whether the alpha is still valid.
4. **Automated Data Fetching:** Automatically pulls Fama-French 3-Factor monthly data directly from Kenneth French's data library.

## Methodology & Intuition
The system evaluates the validity of your alpha using a mix of classical econometrics and Bayesian methods:

* **Rolling OLS Regression:** Extracts the realized alpha by regressing the signal's returns against passive factors (Market-RF, SMB, HML) over a rolling 24-month window.
* **Bayesian Online Change-Point Detection (BOCD):** Uses the Adams & MacKay (2007) algorithm combined with a Normal-Inverse-Gamma (NIG) Conjugate Likelihood. It updates the probability of a change-point at every timestep.
* **Alpha Survival Model:** Models the survival of alpha using an exponential survival model (constant hazard rate) to determine the half-life and output a composite "Alpha Health" score that factors in BOCD survival, statistical significance, and trend.

## Getting Started

### Prerequisites
Ensure you have Python 3 installed along with the required dependencies.

```bash
git clone [https://github.com/zishaan1911/alpha-decay-detection-system.git](https://github.com/zishaan1911/alpha-decay-detection-system.git)
cd alpha-decay-detection
pip install -r requirements.txt
