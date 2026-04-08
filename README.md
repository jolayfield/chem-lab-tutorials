# Computational Chemistry Lab Notebooks

Interactive Jupyter notebooks for students learning computational and data analysis techniques in chemistry. All notebooks run in Google Colab with no local installation required — just click the badge next to any notebook to open it.

---

## How to use these notebooks

1. Click an **Open in Colab** badge below.
2. Run the **first cell** (the setup cell) before anything else. It installs any required packages and sets up data files automatically.
3. Work through the cells in order.

> **Tip for instructors:** Instructor and demo versions of each notebook are available in the `Track1_Gaussian/` and `Track2_MDAnalysis/` folders.

---

## Foundation

| Notebook | Open in Colab |
|----------|--------------|
| Python for Chemists — Part 1: Core Concepts | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/python_for_chemists_part1.ipynb) |

---

## Track 1 — Gaussian 16 Output Analysis

Work with real Gaussian 16 output files using Python. No Gaussian license required — all data files are embedded in the notebooks.

| Notebook | Open in Colab |
|----------|--------------|
| Introduction to Python for Computational Chemistry | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/Track1_Gaussian/gaussian_python_intro.ipynb) |
| Part 2: Parsing Gaussian 16 Output Files | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/Track1_Gaussian/part2_student.ipynb) |
| Part 3: Structure Alignment with AaronTools | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/Track1_Gaussian/part3_student.ipynb) |
| Part 4: Thermochemistry from Gaussian Output | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/Track1_Gaussian/part4_demo.ipynb) |

**Packages installed automatically:** `AaronTools` (Parts 3 only). Parts 1, 2, and 4 use only the Python standard library plus `numpy` and `matplotlib`, which are pre-installed in Colab.

---

## Track 2 — Molecular Dynamics Analysis with MDAnalysis

Analyze MD simulation trajectories using Python. The notebooks use a built-in test trajectory (adenylate kinase, GROMACS format) so you can run every cell without your own simulation data.

| Notebook | Open in Colab |
|----------|--------------|
| Part 1: Core Concepts (Data Analysis) | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/Track2_MDAnalysis/part1_student.ipynb) |
| Introduction to MDAnalysis: Analyzing Peptide Simulations | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/Track2_MDAnalysis/mdanalysis_intro_student.ipynb) |

**Packages installed automatically:** `MDAnalysis`, `MDAnalysisTests`. `numpy` and `matplotlib` are pre-installed in Colab.

---

## Track 3 — PLUMED: Collective Variables and Enhanced Sampling

Learn to use PLUMED with GROMACS for CV analysis and enhanced sampling simulations. Synthetic COLVAR data is generated in the setup cell so every analysis section runs in Colab without a PLUMED or GROMACS installation.

| Notebook | Open in Colab |
|----------|--------------|
| PLUMED: Collective Variables, Analysis, and OPES Enhanced Sampling | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/Track3_PLUMED/plumed_tutorial.ipynb) |

**Topics covered:** `plumed driver` for post-processing trajectories, CV definitions (distances, dihedrals, RMSD, coordination number), OPES_METAD for free energy surfaces along structural CVs, OPES_EXPANDED for multithermal and alchemical expanded ensemble simulations, reweighting, block averaging for uncertainty estimates.

**Packages installed automatically:** `plumed` (Python API). `numpy`, `matplotlib`, and `pandas` are pre-installed in Colab. The standalone `plumed` binary and GROMACS require a separate HPC installation.

---

## Dependencies at a glance

| Package | Version | Installed by setup cell? | Notes |
|---------|---------|--------------------------|-------|
| `numpy` | any | No — pre-installed in Colab | |
| `matplotlib` | any | No — pre-installed in Colab | |
| `pandas` | any | No — pre-installed in Colab | |
| `AaronTools` | ≥ 1.0 | Yes (Track 1, Parts 3) | Gaussian log parsing and geometry tools |
| `MDAnalysis` | ≥ 2.0 | Yes (Track 2 MDAnalysis intro) | MD trajectory analysis |
| `MDAnalysisTests` | ≥ 2.0 | Yes (Track 2 MDAnalysis intro) | Provides built-in test trajectory |
| `plumed` | ≥ 2.7 | Yes (Track 3) | Python API; standalone binary requires HPC install |

---

## Repository structure

```
chem-lab-tutorials/
├── python_for_chemists_part1.ipynb   ← foundation Python
├── Track1_Gaussian/
│   ├── gaussian_python_intro.ipynb
│   ├── part2_student.ipynb           ← student version
│   ├── part2_instructor.ipynb        ← instructor version (solutions)
│   ├── part2_demo.ipynb              ← demo version
│   ├── part3_student.ipynb
│   ├── part3_instructor.ipynb
│   ├── part3_demo.ipynb
│   ├── part4_demo.ipynb
│   ├── water.log                     ← Gaussian output (H2O B3LYP/6-31G*)
│   └── example_freq.log              ← Gaussian frequency output
├── Track2_MDAnalysis/
│   ├── part1_student.ipynb
│   ├── part1_instructor.ipynb
│   ├── mdanalysis_intro_student.ipynb
│   ├── mdanalysis_intro_instructor.ipynb
│   └── mdanalysis_intro_demo.ipynb
└── Track3_PLUMED/
    └── plumed_tutorial.ipynb         ← PLUMED driver, OPES_METAD, OPES_EXPANDED
```

---

*Notebooks developed for the Layfield Research Group. Questions? Contact jolayfield@gmail.com.*
