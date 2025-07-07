# Python Actuarial Calculation Toolkit

A robust, object-oriented Python library for performing fundamental life contingency calculations.

> **⚠️ Project Status: In Progress & Core Functionality Complete**
>
> This project provides a powerful, well-tested `ActuarialCalculator` class. While a full Streamlit user interface is planned for the future, the core calculation engine is complete and functional. The library is under continuous development to expand its feature set.

---
##  About The Project

This library was built to provide a clean, efficient, and accurate tool for calculating the Expected Present Value (EPV) of various insurance and annuity products. It is designed with actuarial students and professionals in mind, emphasizing both correctness and computational performance by leveraging vectorized operations with NumPy and caching for recursive calculations.

The core of the project is the `ActuarialCalculator` class, which takes a standard life table and an interest rate to perform a wide range of calculations.

## Core Features Implemented

* **Insurance Benefits:**
    * Whole Life, Term, and Endowment Insurance
    * Deferred Insurance
    * Support for Annual and M-thly payable benefits (using UDD)
* **Annuities:**
    * Whole Life, Term, and Deferred Annuities
    * Annuities-Certain
    * Guaranteed Annuities
    * Geometrically Increasing Annuities
    * Support for Due and Immediate payments, both Annual and M-thly
* **Efficiency:**
    * Uses backward recursion with caching for efficient `Ax` calculations.
    * Leverages NumPy for vectorized computations where possible.
    * Object-oriented design for clean and reusable code.

---
## Basic Usage

Here is a simple example of how to use the calculator:

```python
import pandas as pd
from actuarial_calculator import ActuarialCalculator

# 1. Load your life table
life_table_data = {'age': [90, 91, 92], 'lx': [1000, 800, 500]}
life_table = pd.DataFrame(life_table_data)

# 2. Initialize the calculator
interest = 0.05
calc = ActuarialCalculator(life_table, interest)

# 3. Perform calculations
# EPV of a 2-year term insurance for a person aged 90
epv_term_insurance = calc.annual_term_insurance(x=90, n=2)
print(f"A^1_{{90:2|}} = {epv_term_insurance:.5f}")

# EPV of a whole life annuity-due for a person aged 90
epv_annuity = calc.whole_life_annuity_due(x=90)
print(f"a_due_{{90}} = {epv_annuity:.5f}")


🗺️ Project Roadmap
The following features are planned for future development:

[ ] Streamlit User Interface: Develop an interactive web app to use the calculator.

[ ] Premium Calculations: Add methods for calculating net and gross premiums.

[ ] Policy Value / Reserve Calculations: Implement functions to calculate policy reserves.

[ ] Unit Testing: Develop a comprehensive suite of tests to validate all calculations against known results.