# Sea Surface Temperature during Indian Ocean Dipole

## Experiment Description

In this project, I investigate the difference in sea surface temperature (SST) patterns between a **positive Indian Ocean Dipole (IOD)** year and a **neutral year** using ocean model simulations.

**Science Question:**
*How does the Indian Ocean Dipole affect the surrounding waters during positive and negative years?*

To explore this, I simulate two years:

* **1996**: A neutral IOD year.
* **1997**: A strong positive IOD year.

Using ECCO Version 5 model data, I examine SST patterns, stratification, and anomalies across the Indian Ocean—particularly the equatorial region, Arabian Sea, Bay of Bengal, and eastern Indian Ocean near Indonesia. The objective is to understand how the IOD modulates ocean temperatures and affects regional climate.

## Steps to Reproduce

### Step 1: Create the Model Input Files

Run the following python notebooks in the `notebooks/` directory in order to generate the model input files:

* `model_grid.ipynb`: Create model grid structure.
* `iod_bathymetry.ipynb`: Generate bathymetry data.
* `initial_conditions_1996.ipynb` & `initial_conditions_1997.ipynb`: Set initial ocean conditions.
* `external_conditions_1996.ipynb` & `external_conditions_1997.ipynb`: Generate surface forcing data (e.g. winds).
* `boundary_conditions_1996.ipynb` & `boundary_conditions_1997.ipynb`: Define open boundary conditions.

All input files should be stored in appropriate subdirectories under `input/` (e.g., `input/exf`, and `input/obcs`).

### Step 2: Transfer Files to the Computing Cluster

```bash
git clone https://github.com/MITgcm/MITgcm.git
mkdir -p MITgcm/configurations/indian_ocean_dipole
```

Copy the following directories using `scp` or your preferred method:

* `code/`
* `input/`
* `namelist/`
* `run/` and `run_1997/`

### Step 3: Compile the Model

```bash
cd MITgcm/configurations/indian_ocean_dipole
mkdir build
cd build
../../../tools/genmake2 -of ../../../tools/build_options/darwin_amd64_gfortran -mods ../code -mpi
make depend
make
```

### Step 4: Run the Model

#### For 1996 (Neutral Year)

```bash
cd run
sbatch cs185c07.slm
```

#### For 1997 (Positive IOD Year)

```bash
cd run_1997
sbatch cs185c07.slm
```

Ensure each run directory has symbolic links to the corresponding `input/` and `code/` directories.

### Step 5: Post-Processing & Analysis

Use the following notebooks for visualization and analysis:

* `model_results_movie_1996.ipynb`
* `model_results_movie_1997.ipynb`
* `answer_science_question.ipynb`

## Results & Analysis

### Sea Surface Temperature Trends

<img width="599" alt="Screenshot 2025-05-18 at 12 39 37 AM" src="https://github.com/user-attachments/assets/777de201-2a04-41e7-864b-7602e6b7e526" />

#### 1996 (Neutral Year – Blue Line)

* Gradual warming begins mid-year, peaking around August–September (\~30.3 °C).
* Steady cooling follows into early 1997, reaching lows around 28.4 °C.
* Pattern reflects **normal seasonal variability** and a **lack of extreme anomalies**, characteristic of a neutral IOD year.

#### 1997 (Positive IOD Year – Red Line)

* SST increases more rapidly than in 1996, peaking \~31.6 °C in September.
* Post-peak cooling is more gradual; temperatures stay elevated compared to 1996.
* From **July to October**, SST anomalies range between **+1.0 to +1.5 °C**, demonstrating strong **positive IOD** conditions.

## Conclusion

The simulation results confirm that the **Indian Ocean Dipole (IOD)** plays a significant role in modulating ocean surface temperatures:

* In a **positive IOD year (1997)**, warm SST anomalies develop in the **western Indian Ocean**, while the **eastern Indian Ocean cools** due to enhanced upwelling and a shoaling thermocline.
* This contrasts with **neutral conditions (1996)**, which show consistent seasonal SST variations without significant anomalies.

These temperature shifts alter **regional weather**:

* **Western basin warming** → Increased rainfall in East Africa.
* **Eastern basin cooling** → Droughts in Indonesia and Australia.

The IOD significantly influences **monsoon strength**, **precipitation patterns**, and **climate variability** across the Indian Ocean rim, reinforcing the importance of understanding and forecasting such events.
