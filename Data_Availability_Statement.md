# Data Availability Statement

**Paper:** Boundary Value Problems of Coupled Generators in Markov-Modulated Diffusions: Theory, Adaptive Algorithms, and their Application in the Computation of First-Passage Time

All code and data needed to reproduce the results in the manuscript are in this repository.

---

## Repository Structure

```
├── generate_validation.py                 # reproduces all figures and tables
├── data/
│   ├── Experimental_data_fresh_cell.csv   # HPPC data, fresh NMC pouch cell
│   ├── Experimental_data_aged_cell.csv    # HPPC data, aged NMC pouch cell
│   ├── OCV_vs_SOC_curve.csv               # measured OCV–SOC curve
│   ├── model_parameters.json              # ECM + CTMC parameters (Table 2, Eq. 16)
│   ├── tte_simulation_results.json        # TTE outputs corresponding to Table 4
│   └── DATA_SUMMARY.md                    # column descriptions for the CSV files
```

---

## Files

### `generate_validation.py` (33.1 KB)
SHA-256: `659208dd5d446c02e9026f438e2180d9db7d2037d7c9b3f3fa653aa378b4c31c`

Single script that reads the data files, runs Nelder–Mead parameter identification, Monte Carlo TTE simulations (N = 2000), and the coupled BVP solver, then writes Figures 1–8 to `figures/` and prints Table 3, 5, 6, 7 values. Table 7 is also saved as a LaTeX fragment.

Requires Python 3.9+ with `numpy`, `scipy`, `pandas`, `matplotlib`.

### `Experimental_data_fresh_cell.csv` (13.68 MB)
SHA-256: `d9f13d3223e8196da1e4a023101c060891106cc12c467b37dbcf4bc01901be6d`

HPPC test recording for a fresh NMC pouch cell. Columns: Time (s), Current (A), Voltage (V), Temperature (°C). Used in Section 5 for ECM parameter identification and in Figure 4a,c (RMSE 5.1 mV).

### `Experimental_data_aged_cell.csv` (13.83 MB)
SHA-256: `e1410f30763501d6d4f345cd0fe887e751d6a270b01bb3b5bdd171863e14603f`

Same format as above, recorded on an aged cell. Used in Figure 4b,d (RMSE 12.0 mV).

### `OCV_vs_SOC_curve.csv` (23.2 KB)
SHA-256: `d7dd665e6d356721ceb08bbbbd3e9f7401bc3cfac0a1b3fbea8df74637a506ea`

Columns: SOC (0–1), V0 (V). Fitted by a 7th-order polynomial (R² = 0.9983, RMSE 9.8 mV; see Figure 3).

### `model_parameters.json` (1.6 KB)
SHA-256: `e8aa77cac1efd5e299b5abaaf08fc24390756b70a897c75ce1cc5617c520c0e7`

Contains the identified ECM parameters from Table 2 (R₀, R₁, R₂, τ₁, τ₂, activation energies, σ_soc) and the CTMC generator matrix Q from Eq. 16 with the stationary distribution and per-mode power levels.

### `tte_simulation_results.json` (1.3 KB)
SHA-256: `d8c745de2cd38fb5e298a54bb9de92c7790b50f264f9e12c6b81e8a51be2c6e7`

Deterministic TTE, MC mean, and 90% CI for each of the five load modes and the mixed-HMM scenario. Values match Table 4 of the manuscript.

### `DATA_SUMMARY.md` (3.1 KB)
SHA-256: `b8af65d9961919b0c992fed90bca35961fbfb75d8e40cb4568a235e0c09192fb`

Plain-text description of column names and data types for all CSV files.

---

## How to reproduce

```bash
python generate_validation.py
```

This reads `data/`, runs the simulations, and writes PDFs to `figures/`. Tested on Python 3.10 / Intel i7-12700H / 32 GB RAM.

## Contact
For questions about the data or code, please contact the corresponding author.
