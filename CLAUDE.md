# CLAUDE.md — Layfield Research Group: chem-lab-tutorials

## Project overview

This repository contains interactive Jupyter notebooks for students learning computational chemistry and molecular simulation analysis. All notebooks are designed to run on **Google Colab** with no local installation — each notebook has a setup cell that installs required packages and embeds or downloads necessary data files.

GitHub repo: `jolayfield/chem-lab-tutorials`
Contact: jolayfield@gmail.com

---

## Repository structure

```
chem-lab-tutorials/
├── python_for_chemists_part1.ipynb   ← Foundation Python (Part 1)
├── Track1_Gaussian/                  ← Gaussian 16 output file analysis
│   ├── gaussian_python_intro.ipynb
│   ├── part2_{student,instructor,demo}.ipynb
│   ├── part3_{student,instructor,demo}.ipynb
│   ├── part4_demo.ipynb
│   ├── water.log                     ← H2O B3LYP/6-31G* Gaussian output
│   └── example_freq.log              ← Gaussian frequency output
├── Track2_MDAnalysis/                ← MD trajectory analysis
│   ├── part1_{student,instructor}.ipynb
│   ├── mdanalysis_intro_{student,instructor,demo}.ipynb
└── Track3_PLUMED/                    ← PLUMED, neural networks, machine-learned CVs
    ├── plumed_tutorial.ipynb
    ├── nn_intro_pytorch.ipynb
    └── mlcolvar_deeplda_deeptica.ipynb
```

Note: some notebooks are duplicated at the repo root (e.g., `part1_student.ipynb`, `part2_student.ipynb`, `gaussian_python_intro.ipynb`, `water.log`). The canonical versions live in their respective `Track*/` folders.

---

## Notebook conventions

**Three variants exist for most notebooks:**
- `*_student.ipynb` — exercises with `None` stubs and `raise NotImplementedError()` placeholders
- `*_instructor.ipynb` — full solutions; not shared publicly
- `*_demo.ipynb` — instructor-facing walkthrough version

**Setup cell:** Every notebook begins with a `# COLAB SETUP` code cell that must be run first. It installs packages and embeds/writes data files (e.g., `water.log`) directly so no external downloads are needed.

**Exercise pattern:** Student notebooks use this pattern throughout:
```python
result = None          # replace with your code
raise NotImplementedError()
```
followed by a "Test" cell that validates the student's answer.

---

## Tracks and dependencies

### Track 1 — Gaussian 16 Output Analysis
Parse real Gaussian `.log` files using only the Python standard library + numpy + matplotlib. Parts 1, 2, and 4 require no extra installs. Part 3 installs `AaronTools` for geometry manipulation.

Key topics: SCF energy extraction, thermochemical data parsing, normal termination verification, Standard orientation geometry, bond lengths/angles, AaronTools structure alignment.

### Track 2 — Molecular Dynamics Analysis (MDAnalysis)
Analyze MD trajectories. Uses the built-in adenylate kinase test trajectory (GROMACS format) from `MDAnalysisTests` — no user-supplied simulation data required.

Setup installs: `MDAnalysis`, `MDAnalysisTests`

### Track 3 — PLUMED, Neural Networks, and Machine-Learned CVs
Recommended order: PLUMED tutorial → NN intro → mlcolvar notebook.

- **PLUMED notebook:** `plumed driver`, CV definitions, OPES_METAD, OPES_EXPANDED, reweighting, block averaging. Installs: `plumed` (Python API only; standalone binary requires HPC).
- **NN intro:** Single neuron math through PyTorch training loops; backpropagation derivation with numerical verification; neural network potentials overview. Installs: `torch`.
- **mlcolvar notebook:** Deep-LDA, Deep-TICA, PLUMED export via TorchScript; uses synthetic alanine dipeptide data. Installs: `mlcolvar`, `lightning`.

---

## Dependencies

| Package | Installed by setup cell? | Notes |
|---------|--------------------------|-------|
| `numpy`, `matplotlib`, `pandas` | No — pre-installed in Colab | |
| `AaronTools` (≥ 1.0) | Yes | Track 1, Part 3 only |
| `MDAnalysis` (≥ 2.0) | Yes | Track 2 |
| `MDAnalysisTests` (≥ 2.0) | Yes | Track 2 — provides test trajectory |
| `plumed` (≥ 2.7) | Yes | Track 3 PLUMED; Python API only |
| `torch` (≥ 2.0) | Yes | Track 3 NN intro; often pre-installed on Colab |
| `mlcolvar` (≥ 1.3) | Yes | Track 3 mlcolvar |
| `lightning` (≥ 2.0) | Yes | Track 3 mlcolvar |

---

## How to work with this repo

- **Editing notebooks:** Make changes in the appropriate `Track*/` folder. Keep student/instructor/demo versions in sync when updating exercise content or solutions.
- **Data files:** Gaussian log files (`water.log`, `example_freq.log`) are embedded in notebooks via setup cells. If you update a log file, update the embedded string in the setup cell as well.
- **Adding a new notebook:** Follow the existing naming pattern (`part{N}_{student,instructor,demo}.ipynb`), include a `# COLAB SETUP` cell as cell 0, and add a Colab badge link to `README.md`.
- **No local Python environment is configured** — notebooks are written for Colab. If running locally, install dependencies manually.

---

## Git conventions

- Main branch: `main`
- Remote: `origin` (GitHub)
- Commit messages describe what was added/changed at the track level (e.g., "Add Track3_PLUMED: PLUMED driver, OPES_METAD, and OPES_EXPANDED tutorial")
- `.gitignore` excludes: `.ipynb_checkpoints/`, `*.pyc`, `__pycache__/`, macOS artifacts, Python virtual environments, AaronTools cache (`AARONLIB/`), and Gaussian scratch files (`*.chk`, `*.fchk`, `*.rwf`, etc.)
