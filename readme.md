# PAAC Assignment 3 – Scalable Quantum Tomography Pipelines

This repository contains the complete implementation for **PAAC Assignment 3**,
focused on building **scalable, reproducible quantum tomography pipelines** that
support increasing qubit counts, persistent model checkpoints, and empirical
scalability analysis.

The project extends earlier tomography setups by introducing:
- Serialization of trained helpers
- Configurable n-qubit surrogate models
- Scalability benchmarks (fidelity and runtime)
- Ablation studies on architectural design choices

All experiments are implemented in a single executable notebook and are fully
reproducible.

---

## Project Overview

Quantum State Tomography becomes exponentially harder as the number of qubits
increases. This assignment investigates how simple surrogate models behave as
system size and architectural complexity grow.

Key objectives:
- Design an extendable n-qubit tomography surrogate
- Serialize trained models for reuse and reproducibility
- Measure how fidelity and runtime scale with qubit count
- Study architectural trade-offs using ablation experiments
- Visualize and document scalability limits

---

## Repository Structure

PAAC_Assignment_3/
│
├── docs/
│ └── report.md # Full experimental report and analysis
│
├── models/
│ ├── README.md # Checkpoint documentation
│ └── model_roundtrip_2.pkl # Example serialized model
│
├── notebooks/
│ └── assignment_3_scalable_tomography.ipynb
│
├── results/
│ └── scalability_results.csv # CSV output for scalability plots
│
└── README.md # Project overview (this file)


---

### 1. Clone the Repository
```bash
git clone <repository-url>
cd PAAC_Assignment_3

```
### 2. Create a Virtual Environment (Recommended)
```
python -m venv venv
# Windows
venv\Scripts\activate
# Linux / macOS
source venv/bin/activate
```

### 3. Install Dependencies
```
pip install numpy pandas matplotlib
No GPU or external quantum libraries are required.
```
## How to Run the Project

All experiments are executed through a single Jupyter notebook.

### 1. Open the Notebook

Open the following notebook:
notebooks/assignment_3_scalable_tomography.ipynb
Alternatively, you can open it using **JupyterLab** or the **VS Code notebook interface**.

### 2. Restart the Kernel

Before running the notebook, restart the kernel to ensure a clean execution state.

### 3. Run All Cells (Top → Bottom)

Running all cells will:

- Demonstrate pickle-based save/load round-trip
- Generate and save model checkpoints in `models/`
- Run scalability experiments over increasing qubits
- Save results to `results/scalability_results.csv`
- Generate fidelity and runtime plots
- Perform ablation studies over model depth

## Experiments Included

### 1. Serialization Demonstration

- Demonstrates saving and loading model objects using `pickle`
- Checkpoints are stored in the `models/` directory
- Naming convention:
model_<track>_<nqubits>.pkl


### 2. Scalability Study

- Varies the number of qubits (`n = 1` to `4`)
- Metrics measured:
- Mean fidelity
- Fidelity variance
- Mean runtime
- Results are saved as CSV files and visualized using plots

### 3. Ablation Study

- Varies architectural depth (number of layers)
- Metrics measured:
- Fidelity
- Fidelity variance
- Runtime
- Demonstrates diminishing returns as model depth increases

---

## Results Summary

### Scalability (Qubits)

- Perfect fidelity achieved for small qubit counts
- Runtime is negligible at low dimensionality
- Confirms correctness of the pipeline for small `n`

### Ablation (Layers)

- Increasing depth initially improves model expressibility
- Fidelity saturates and fluctuates beyond moderate depth
- Runtime overhead dominates at small scales

Detailed tables, plots, and analysis are available in:

📄 **`docs/report.md`**

---

## Reproducibility

- All experiments are deterministic given fixed random seeds
- Serialized checkpoints allow exact restoration of models
- CSV outputs enable downstream plotting and analysis
- No external data or internet access required after setup

---

## Limitations and Future Work

### Current Limitations

- Statevector-based models scale exponentially with qubit count
- No explicit noise or hardware constraints are modeled

### Future Extensions

- Classical shadow tomography
- Measurement-efficient estimators
- Noise-aware models
- Hardware-in-the-loop validation

---

## Author

**Kanishka Gupta**

Developed as part of the **PAAC Open Project (Winter 2025–2026)**.

This project focuses on **scalable quantum tomography**, **reproducibility**, and **empirical analysis** of how model design choices impact performance as quantum system size increases.

