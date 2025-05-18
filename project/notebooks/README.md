# Model Notebooks

This directory contains Jupyter notebooks used to set up, run, and analyze an ocean model simulation focused on the **Indian Ocean Dipole (IOD)**. The simulations compare conditions during a **neutral year (1996)** and an **IOD event year (1997)**.

### Model Setup Notebooks

| Notebook               | Description                                                                                           |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| `model_grid.ipynb`     | Generates the model grid for the Indian Ocean domain. Defines resolution, extent, and grid structure. |
| `iod_bathymetry.ipynb` | Constructs bathymetry (ocean floor depth) data for the model using IOD-specific topographic data.     |


### Initial and Boundary Conditions

These notebooks define the ocean's initial state and boundary interactions for each year.

| Notebook                         | Description                                                                                 |
| -------------------------------- | ------------------------------------------------------------------------------------------- |
| `initial_conditions_1996.ipynb`  | Sets up the initial temperature, salinity, and velocity fields for the neutral year (1996). |
| `initial_conditions_1997.ipynb`  | Sets up the initial state for the IOD event year (1997).                                    |
| `boundary_conditions_1996.ipynb` | Prepares open boundary conditions (e.g., temperature, salinity, velocities) for 1996.       |
| `boundary_conditions_1997.ipynb` | Same as above, but for the 1997 simulation.                                                 |


### External Forcing Conditions

These notebooks prepare the surface forcing such as wind stress, heat flux, and freshwater flux for each year.

| Notebook                         | Description                                                                  |
| -------------------------------- | ---------------------------------------------------------------------------- |
| `external_conditions_1996.ipynb` | Generates surface forcing data (wind, heat, etc.) for the 1996 neutral year. |
| `external_conditions_1997.ipynb` | Generates forcing fields for the 1997 IOD event year.                        |


### Model Output Analysis

| Notebook                         | Description                                                                          |
| -------------------------------- | ------------------------------------------------------------------------------------ |
| `model_results_movie_1996.ipynb` | Processes and visualizes the 1996 simulation outputs. Generates animations or plots. |
| `model_results_move_1997.ipynb`  | Processes outputs from the 1997 simulation. Similar analyses for IOD impact.         |


### Scientific Question

| Notebook                        | Description                                                                                                                                                |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `answer_science_question.ipynb` | Synthesizes model results to answer the main scientific question related to the Indian Ocean Dipole. Summarizes differences between neutral and IOD years. |
