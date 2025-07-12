# Central Difference Method for SDOF System Analysis

This Jupyter Notebook provides a Python implementation of the **Central Difference Method** to determine the dynamic response of a Single-Degree-of-Freedom (SDOF) system subjected to earthquake ground motion.

The analysis uses the classic **1940 El Centro earthquake** dataset as the input ground motion.

---
## Results

![El-Centro Graphs](output.png)
---

---
## Key Concepts

The core of this analysis is the Central Difference Method, a powerful and straightforward numerical technique for solving the equation of motion for a dynamic system. This method approximates the velocity and acceleration at a given time step using the displacements at adjacent time steps.

The fundamental equation of motion being solved is:

$$m\ddot{u}(t) + c\dot{u}(t) + ku(t) = P(t) = -m\ddot{u}_g(t)$$

Where:
- $m$ = Mass of the system
- $c$ = Damping coefficient
- $k$ = Stiffness of the system
- $\ddot{u}(t), \dot{u}(t), u(t)$ = Acceleration, velocity, and displacement of the mass relative to the ground
- $P(t)$ = Effective load due to ground acceleration, $\ddot{u}_g(t)$

---
## Methodology

The notebook is structured to follow the logical steps of a dynamic analysis using the Central Difference Method:

1.  **Parameter Initialization**: Key structural properties (**Stiffness `k`**, **Mass `m`**, and **Damping Ratio `dr`**) are defined. From these, derived properties like natural frequency ($\omega_n$), natural period ($T_n$), and the damping coefficient ($c$) are calculated.

2.  **Data Loading**: The El Centro ground acceleration data is loaded from the `Data_Elcentro.csv` file using the `pandas` library.

3.  **Initial Calculations**: The initial conditions (displacement $u_0$ and velocity $v_0$) are set to zero. The algorithm is kick-started by calculating the displacement at a fictitious previous time step ($u_{-1}$) and the effective load ($P_i$). Key constants for the method ($\hat{k}, a, b$) are also computed.

4.  **Iterative Solution**: A `for` loop iterates through each time step of the earthquake record. In each iteration, it calculates the displacement for the next time step ($u_{i+1}$) based on the current and previous displacements ($u_i, u_{i-1}$) and the effective load at that step.

5.  **Visualization**: After the loop completes, the results are processed and visualized using `matplotlib`. The notebook generates four plots to show the system's response over time:
    - Ground Acceleration vs. Time
    - Relative Displacement vs. Time
    - Relative Velocity vs. Time
    - Relative Acceleration vs. Time

---
## How to Use

To run this analysis, follow these steps:

1.  **Prerequisites**: Ensure you have Python and the required libraries installed.
    ```bash
    pip install numpy pandas matplotlib
    ```

2.  **Input File**: Place the `Data_Elcentro.csv` file in the same directory as the Jupyter Notebook.

3.  **Execution**: Open the `Central Difference Method.ipynb` file in a Jupyter environment and run the cells in order from top to bottom.

---
## Customization

You can easily adapt this notebook to analyze different SDOF systems or use other earthquake records:

-   **Structural Properties**: Modify the `k`, `m`, and `dr` variables in the **Initial Parameters** section to match the properties of your structure.
-   **Earthquake Data**: Replace `Data_Elcentro.csv` with another ground motion file. Ensure the file is a CSV with "time" and "acceleration" columns.
