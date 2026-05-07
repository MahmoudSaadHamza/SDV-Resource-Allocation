# SDV Resource Allocation — Adaptive Metaheuristics, Hybrid Methods, and Learned Method Selection

Code and benchmarks for the IEEE conference paper *"Adaptive Metaheuristics, Hybrid Methods, and Learned Method Selection for Resource Allocation in Software-Defined Vehicles"* by Mahmoud S. Hamza, Ousman Khan, and Alaa Khamis (KFUPM AI for Smart Mobility Lab).

## What's here

A single self-contained Jupyter notebook, [`sdv_resource_allocation.ipynb`](sdv_resource_allocation.ipynb), that implements all proposed methods, generates the synthetic benchmark, runs the cross-validated evaluation, and produces every figure and table reported in the paper:

- **CSCH-Guided** constructive baseline (Khan & Khamis, 2025)
- **Adaptive Simulated Annealing** with reactive cooling
- **Adaptive Tabu Search** with reactive tabu length
- **Adaptive Genetic Algorithm** with component-wise crossover and adaptive mutation
- **H-Comp / H-Nest** memetic matheuristic hybrid (CSCH-Guided + ILP local search)
- **Path-A ILP** exact reference (Pan et al., 2022)
- **Random Forest method selector** with 19 instance features

## How to run

### Option 1 — Google Colab (recommended)

Click the badge below to open the notebook in Colab. Set `QUICK_DEMO = True` (default) for a 10-minute end-to-end verification run, or `QUICK_DEMO = False` to reproduce the full paper benchmark.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MahmoudSaadHamza/SDV-Resource-Allocation-Final/blob/main/sdv_resource_allocation.ipynb)

### Option 2 — local Jupyter

```bash
git clone https://github.com/YOUR-USERNAME/SDV-Resource-Allocation-Final.git
cd SDV-Resource-Allocation-Final
pip install -r requirements.txt
jupyter notebook sdv_resource_allocation.ipynb
```

## Requirements

- Python 3.9 or newer
- A working Gurobi installation. The free academic license is sufficient for the largest instance ($n = 800$); the size-limited free license will fail on instances above ≈ 100 applications. Get an academic license at https://www.gurobi.com/academia/academic-program-and-licenses/.

All other dependencies are listed in [`requirements.txt`](requirements.txt).

## Reproducibility

All benchmark instances are synthetic and parameterised by fixed seeds. No external data download is required — running the notebook from a fresh clone reproduces every number reported in the paper. The synthetic generator covers five problem sizes ($n \in \{100, 200, 400, 600, 800\}$) and five density combinations per size, yielding 48 feasible instances under the 80-VM cap.

## Runtime

| Mode | Instances | Approximate runtime (Colab CPU) |
|---|---|---|
| `QUICK_DEMO = True`  | 3  | 10 minutes |
| `QUICK_DEMO = False` | 48 | 3–4 hours |

The bottleneck is the Path-A ILP at $n \geq 600$ (120-second time-limit cap per instance).

## Citation

If you use this code, please cite the paper:

```bibtex
@inproceedings{hamza2026adaptive,
  title  = {Adaptive Metaheuristics, Hybrid Methods, and Learned Method
            Selection for Resource Allocation in Software-Defined Vehicles},
  author = {Hamza, Mahmoud S. and Khan, Ousman and Khamis, Alaa},
  year   = {2026}
}
```

## License

MIT — see [`LICENSE`](LICENSE).
