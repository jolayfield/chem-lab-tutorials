---
name: sync-variants
description: Sync student/instructor/demo notebook variants for a given notebook base name. Checks that student stubs are blanked, solutions match instructor, and demo cells are coherent.
---

The user will name a notebook base (e.g. "part2", "mlcolvar_deeplda_deeptica", or a Track folder like "Track1_Gaussian/part3").

## Your job

1. **Find all variants** — search the repo for `*_student.ipynb`, `*_instructor.ipynb`, `*_demo.ipynb` matching the base name (check both the Track subfolder and the repo root).
2. **Compare cell-by-cell** — for each code cell in the instructor notebook:
   - Student version should replace the solution body with exactly:
     ```python
     result = None  # replace with your code
     raise NotImplementedError()
     ```
   - Demo version should contain the solution and may have extra markdown explanation cells inserted.
   - Markdown/text cells should be identical across all three variants unless intentionally different (e.g. demo has extra notes).
3. **Report mismatches** — list: notebook name, cell id or index, and a short description of what's wrong. Examples:
   - "student cell #5 contains solution code that should be stubbed"
   - "instructor cell #8 is missing from student notebook"
   - "demo cell #3 markdown differs from instructor without explanation"
4. **Ask the user which direction to sync** before making any changes:
   - instructor → student (blank out student stubs to match instructor solutions)
   - instructor → demo (update demo to match instructor solutions)
   - flag only (report mismatches, no edits)
5. **Apply the sync** if the user confirms, editing only the target variant.

## Notebook JSON structure reminder

Jupyter notebooks are JSON. Each cell has:
- `"cell_type"`: `"code"` or `"markdown"`
- `"source"`: list of strings (lines of the cell)
- `"id"`: stable identifier if present

When stubbing a student cell, replace only the `"source"` lines that contain the solution. Keep any leading docstring or comment lines that explain the exercise. Remove any `"outputs"` and set `"execution_count"` to `null` in student cells.
