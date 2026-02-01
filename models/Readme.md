# Model Checkpoints

This directory contains serialized quantum tomography model checkpoints produced
during **PAAC Assignment 3: Scalable Quantum Tomography Pipelines**.

The checkpoints allow trained surrogate models to be saved, restored, and reused
across experiments to ensure reproducibility and consistent evaluation.

---

## Naming Convention

All checkpoint files follow the required naming scheme:
model_<track>_<nqubits>.pkl
### Example

- `model_roundtrip_2.pkl`  
  → A serialized 2-qubit surrogate model used to demonstrate save/load  
  round-trip functionality.

---

## What Each `.pkl` File Contains

Each pickle file stores a **fully restorable model object**, including:

- Number of qubits (`n_qubits`)
- Architectural configuration (e.g., number of layers)
- Model parameter vectors
- Random seed used for initialization
- Metadata required for fidelity evaluation

The stored object can be reconstructed exactly as it was at save time.

---

## How to Load a Checkpoint

Models can be restored using the provided helper methods:

```python
from QuantumModel import QuantumModel

model = QuantumModel.load("models/model_roundtrip_2.pkl")
Once loaded, the model supports:

- Statevector reconstruction
- Fidelity computation against target states
- Reuse in scalability or ablation experiments

---
```
## Serialization Format Notes

- Python’s `pickle` module is used for serialization
- Pickle enables fast and exact object restoration
- Suitable for research and prototyping workflows

For long-term storage, large datasets, or cross-language compatibility,  
structured formats such as **HDF5** would be preferable.

---

## Usage Notes

- Do not manually edit `.pkl` files
- Regenerate checkpoints by re-running the notebook if needed
- All committed checkpoints correspond to executed notebook outputs

