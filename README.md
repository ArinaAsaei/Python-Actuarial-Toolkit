# Python Actuarial Calculation Toolkit

A robust, object-oriented Python library for performing fundamental life contingency calculations, with advanced support for select and ultimate mortality models.

> **⚠️ Project Status: In Progress**
>
> The core `ActuarialCalculator` engine is complete and functional. A full Streamlit user interface is planned for the future.

---

## About The Project

This library provides a clean, efficient, and accurate tool for calculating the Expected Present Value (EPV) of various insurance and annuity products. It's designed to handle complex, modern actuarial models by separating the mortality logic from the financial calculations, making it both powerful and easy to use.

## Key Features

* **Flexible Mortality Models:**
    * **Tabular:** Load standard ultimate or select & ultimate life tables directly from a pandas DataFrame.
    * **Parametric:** Generate complete select & ultimate tables on-the-fly from Makeham's Law parameters and select period modifiers.

* **Unified Product API:**
    * Single, powerful methods like `term_annuity`, `whole_life_insurance`, and `deferred_annuity` handle all variations (due/immediate, annual/m-thly, term/whole life) through intuitive parameters.

* **Comprehensive Product Coverage:**
    * Life Insurances: Whole Life, Term, Endowment, and Deferred.
    * Life Annuities: Whole Life, Term, Deferred, and Guaranteed.
    * Annuities-Certain and Geometrically Increasing Annuities.

* **Performance Optimized:**
    * Uses backward recursion with caching for efficient `Ax` calculations.
    * Leverages NumPy for vectorized computations where possible.

---

## Installation

1.  Clone the repository:
    ```sh
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    ```
2.  Install dependencies (ensure you have a `requirements.txt` file with `pandas` and `numpy`):
    ```sh
    pip install -r requirements.txt
    ```

---

## Usage Examples

Here are a few examples demonstrating the calculator's flexibility.

### Example 1: Standard Ultimate Table

```python
import pandas as pd
from actuarial_calculator import ActuarialCalculator

# 1. Define a simple life table
simple_table_df = pd.DataFrame({
    'age': range(90, 96),
    'lx': [1000, 800, 600, 400, 200, 50]
})

# 2. Initialize the calculator in 'ultimate_tabular' mode
calc_simple = ActuarialCalculator(
    interest_rate=0.06,
    mode='ultimate_tabular',
    data={'table': simple_table_df}
)

# 3. Perform a calculation
epv_annuity = calc_simple.term_annuity(x=90, n=2, timing='due')
print(f"ä_90:2| = {epv_annuity:.5f}")
```
---
## 🗺️ Project Roadmap
The following features are planned for future development:

[ ] Streamlit User Interface: Develop an interactive web app to use the calculator.

[ ] Premium Calculations: Add methods for calculating net and gross premiums.

[ ] Policy Value / Reserve Calculations: Implement functions to calculate policy reserves.

[ ] Unit Testing: Develop a comprehensive suite of tests to validate all calculations against known results.