# Sea Surface Temperature during Indian Ocean Dipole

## Experiment Description

In this project, I will investigate the difference in Indian Ocean Dipoles between a positive and negative year. In particular, I will investigate the following science question:

_How does the Indian Ocean Dipole affect the surrounding waters during positive and negative years?_

This model experiment investigates the impact of the **Indian Ocean Dipole (IOD)** on sea surface temperature by comparing two years: **1997**, a strong positive IOD year, and **1996**, a neutral year. The region of interest spans the equatorial and western Indian Ocean, including the Arabian Sea, Bay of Bengal, and waters near Indonesia. Using ECCO Version 5 model data, I will simulate SST patterns and ocean stratification for both years. The experiment will analyze temperature anomalies, vertical temperature profiles, and spatial SST distributions. I anticipate that 1997 will show significant cooling in the western Indian Ocean due to strong upwelling, while the eastern Indian Ocean will experience warming as upwelling weakens and the thermocline deepens. In contrast, 1996 should exhibit more stable SST patterns with weaker temperature gradients. By comparing these two years, this study will highlight the IOD’s role in modulating ocean temperatures and circulation patterns in the Indian Ocean basin.

## Steps to Reproduce

The following steps outline how to recreate the model files, compile and run the model, and assess outputs for the **Indian Ocean Dipole simulations**, including runs for a **neutral year (1996)** and an **IOD year (1997)**.

### Step 1: Create the Model Input Files

Generate the necessary model input files using the provided notebooks in the `notebooks/` directory:

* **Bathymetry** – `notebooks/iod_bathymetry.ipynb`
* **Initial Conditions** – `notebooks/initial_conditions_1996.ipynb` and `notebooks/initial_conditions_1997.ipynb`
* **External Forcing Conditions** – `notebooks/external_conditions_1996.ipynb` and `notebooks/external_conditions_1997.ipynb`. The external forcing conditions should be in a directory such as `input/exf`.
* **Boundary Conditions** – `notebooks/boundary_conditions_1996.ipynb` and `notebooks/boundary_conditions_1996.ipynb`. The boundary conditions should be in a directory such as `input/obcs`.

Ensure the generated files are organized in the `input/` folder

### Step 2: Transfer Files to the Computing Cluster

1. SSH into your computing cluster.

2. Clone MITgcm to your scratch or home directory (if not already done):

   ```bash
   git clone https://github.com/MITgcm/MITgcm.git
   ```

3. Make a directory for your model configuration:

   ```bash
   mkdir -p MITgcm/configurations/indian_ocean_dipole
   ```

4. Use `scp` or another file transfer tool to copy the following to the `indian_ocean_dipole` directory:

   * `code/`
   * `input/`
   * `namelist/`
   * `run/` and `run_1997/` (run scripts)

### Step 3: Compile the Model

Once on the cluster and inside the `indian_ocean_dipole/` directory:

1. Create a `build/` directory:

   ```bash
   mkdir build
   cd build
   ```

2. Compile the model:

   ```bash
   ../../../tools/genmake2 -of ../../../tools/build_options/darwin_amd64_gfortran -mods ../code -mpi
   make depend
   make
   ```

### Step 4: Run the Model

Move into the run directory and submit the job script for the desired year:

#### Run for 1996 (Neutral Year)

```bash
cd run
sbatch cs185c07.slm
```

#### Run for 1997 (IOD Year)

```bash
cd run_1997
sbatch cs185c07.slm
```

Ensure that symbolic links to the corresponding `input/` and `code/` folders are correctly set up in each run directory.

### Step 5: Post-Processing & Analysis

After the simulation completes, analyze the output files located in the respective run directories using notebooks like `notebooks/model_results_movie_1997.ipynb`, `notebooks/model_results_movie_1997.ipynb`, and `notebooks/answer_science_question.ipynb` for visualizations and comparisons.


