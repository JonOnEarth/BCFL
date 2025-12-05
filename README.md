# BCFL

This repository contains the reference implementation for the algorithms presented in the paper:

A Bayesian Framework for Clustered Federated Learning  
Peng Wu, Tales Imbiriba, Pau Closas  
IEEE Transactions on Pattern Analysis and Machine Intelligence (TPAMI), PrePrints pp. 1–12  
DOI Bookmark: 10.1109/TPAMI.2025.3637562  
IEEE page: https://www.computer.org/csdl/journal/tp/5555/01/11269740/2bXKWIEqFDW  
Preprint (arXiv): https://arxiv.org/abs/2410.15473

The codebase was initially adopted from FedBase (https://github.com/jsmjie/FedBase) and extended to implement and evaluate the BCFL family of algorithms, including algorithmic variants and fixes.

Key implementations:
- BCFL-G — Graph / GNN-based variant (GNN.py)
- BCFL-C — JPDA-based clustering variant (jpda.py)
- BCFL-MH — Multiple-hypothesis (MHT) based variant (mht.py)

---

## Table of contents

- [Overview](#overview)
- [Quick start](#quick-start)
- [Repository structure](#repository-structure)
- [Running examples](#running-examples)
- [Configuration](#configuration)
- [Datasets](#datasets)
- [Reproducing results](#reproducing-results)
- [Citation](#citation)
- [Acknowledgements](#acknowledgements)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

BCFL implements the algorithms and experiment scripts used to evaluate the Bayesian clustered federated learning framework described in the paper. The goal of this repository is to provide a clear, reproducible reference implementation for researchers and practitioners interested in clustered federated learning and federated Bayesian inference.

Primary features:
- Reference implementations for BCFL variants (GNN, JPDA, MHT).
- Example configs and CLI entrypoints for training and evaluation.
- Utilities for data handling, experiment logging, and result aggregation.

---

## Quick start

1. Clone the repository:
```bash
git clone https://github.com/JonOnEarth/BCFL.git
cd BCFL
```

2. Create and activate a virtual environment, then install dependencies:
```bash
python -m venv venv
source venv/bin/activate   # Linux / macOS
venv\Scripts\activate      # Windows

pip install -r requirements.txt
```

3. Run an example experiment (adjust config paths as necessary):
```bash
python GNN.py --config configs/gnn.yaml
python jpda.py --config configs/jpda.yaml
python mht.py --config configs/mht.yaml
```

---

## Repository structure

- `GNN.py` — BCFL-G implementation and experiment entrypoint.
- `jpda.py` — BCFL-C (JPDA) implementation and entrypoint.
- `mht.py` — BCFL-MH (MHT) implementation and entrypoint.
- `configs/` — Example configuration files for experiments.
- `data/` — Data loaders and dataset preparation utilities.
- `scripts/` — Helper scripts for preprocessing, evaluation, and plotting.
- `utils/` — Utilities for logging, checkpoints, and common helpers.
- `README.md` — This file.

If any of these directories are missing in the current tree, please check the repository root for alternate layouts or add the necessary components.

---

## Running examples

Command templates — adapt flags and config paths to your environment.

Run BCFL-G (GNN-based):
```bash
python GNN.py --config configs/gnn.yaml --device cuda:0 --seed 42
```

Run BCFL-C (JPDA-based):
```bash
python jpda.py --config configs/jpda.yaml --device cpu --seed 0
```

Run BCFL-MH (MHT-based):
```bash
python mht.py --config configs/mht.yaml --device cuda:0 --seed 123
```

Common flags (script-specific):
- `--config` : path to YAML/JSON configuration file
- `--dataset` : dataset name or path
- `--device`  : compute device (cpu or cuda)
- `--seed`    : random seed for reproducibility
- `--output`  : directory for logs and checkpoints

---

## Configuration

Use the `configs/` directory to store experiment settings. Typical options include:
- model architecture and hyperparameters
- optimizer settings (learning rate, batch size, weight decay)
- federated settings (number of clients, rounds, local epochs)
- dataset paths and preprocessing options
- logging/checkpoint directories

Example (YAML snippet):
```yaml
dataset: my_dataset
model:
  type: gnn
  hidden_dim: 128
training:
  lr: 1e-3
  epochs: 100
federation:
  clients: 10
  rounds: 50
```

---

## Datasets

This repository does not include large datasets. Consult the paper for datasets used in experiments and prepare local copies following the loader expectations in `data/`. If the paper uses public datasets, links and preprocessing instructions are available in the manuscript.

---

## Reproducing results

To reproduce the experiments from the paper:
1. Prepare datasets in the expected formats and update config files accordingly.
2. Use the example configs in `configs/` or adapt them to match the experimental setup described in the paper.
3. Run training/evaluation scripts and collect logs/checkpoints.

If you reproduce experiments or obtain new results, please consider opening an issue or a pull request with the details so others can benefit.

---

## Citation

If you use this code in your research, please cite the paper:

BibTeX:
```bibtex
@article{wu2025bayesian,
  title = {A Bayesian Framework for Clustered Federated Learning},
  author = {Peng Wu and Tales Imbiriba and Pau Closas},
  journal = {IEEE Transactions on Pattern Analysis and Machine Intelligence},
  year = {2025},
  note = {Accepted. PrePrints pp. 1--12},
  doi = {10.1109/TPAMI.2025.3637562},
  url = {https://www.computer.org/csdl/journal/tp/5555/01/11269740/2bXKWIEqFDW}
}
```

Repository:
```
https://github.com/JonOnEarth/BCFL
```

---

## Acknowledgements

This repository was initially adopted from FedBase (https://github.com/jsmjie/FedBase). We thank the FedBase authors for their code and design. Portions of the code were adapted and extended to implement the BCFL methods.

---

## Contributing

Contributions are welcome. Ways to help:
- Report reproducibility issues via GitHub Issues.
- Submit experimental configs, logs, or scripts to improve reproducibility.
- Open PRs to fix bugs, add tests, or improve documentation.

Suggested workflow:
1. Fork the repository.
2. Create a feature branch.
3. Open a pull request describing the change.

---

## License

See the `LICENSE` file in the repository root for license terms. If no LICENSE file is present, contact the repository owner for usage permissions.

GitHub: https://github.com/JonOnEarth/BCFL

For questions about reproducing the experiments, please open an issue or contact the paper authors listed above.
