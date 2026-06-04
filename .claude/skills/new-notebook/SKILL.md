---
name: new-notebook
description: Scaffold a new set of student/instructor/demo notebooks for a given track and topic. Creates all three variants with the standard COLAB SETUP cell and exercise pattern.
---

The user will provide (or you should ask for):
- **Track folder**: `Track1_Gaussian`, `Track2_MDAnalysis`, or `Track3_PLUMED`
- **Notebook name**: e.g. `part5` (becomes `part5_student.ipynb`, `part5_instructor.ipynb`, `part5_demo.ipynb`)
- **Topic/title**: short description used in the notebook title cell
- **Packages to install in setup cell**: list any beyond what Colab pre-installs (numpy, matplotlib, pandas are pre-installed)

## Steps

1. **Read an existing notebook from the same track** to use as a setup cell template. Pick the most recent `*_instructor.ipynb` in that track folder. Extract cell 0 (the `# COLAB SETUP` cell) as the base.

2. **Adapt the setup cell** for the new notebook: update the package list per user input; keep the same install-and-verify pattern.

3. **Create three notebooks** following the conventions in `CLAUDE.md`:

### `*_instructor.ipynb`
- Cell 0: COLAB SETUP (adapted)
- Cell 1: Markdown title cell — `# Track N — [Topic Title]`
- Cell 2+: Placeholder exercise cells with full solution code and explanatory markdown. Use the comment `# Exercise N:` to mark each exercise.

### `*_student.ipynb`
- Identical structure to instructor, but each exercise code cell body is replaced with:
  ```python
  result = None  # replace with your code
  raise NotImplementedError()
  ```
- All `"outputs"` arrays are empty, `"execution_count"` is `null`.
- A "Test" markdown+code cell pair follows each exercise, pre-filled with validation logic (e.g. `assert result is not None`).

### `*_demo.ipynb`
- Identical to instructor but with additional markdown cells before each exercise explaining the concept and expected output.

4. **Write all three files** into the specified Track folder.

5. **Remind the user** to:
   - Add the three Colab badge links to `README.md` (pattern: `https://colab.research.google.com/github/jolayfield/chem-lab-tutorials/blob/main/<TrackFolder>/<name>_student.ipynb`)
   - Run the setup cell locally or on Colab to verify the install step works.

## Notebook JSON template

Use the standard Jupyter nbformat 4.5 JSON structure:
```json
{
 "nbformat": 4,
 "nbformat_minor": 5,
 "metadata": {
  "kernelspec": {"display_name": "Python 3", "language": "python", "name": "python3"},
  "language_info": {"name": "python", "version": "3.10.0"}
 },
 "cells": []
}
```
