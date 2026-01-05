# Santa Tree Packing Optimization — Kaggle Competition.

## Overview
This repository contains a geometry-based solver for a Kaggle packing puzzle. The goal is to place Christmas tree ornaments without overlaps while minimizing the side length of the smallest square that bounds all trees.

## Objective
- Place N trees (N = 1..200) with positions and rotations.
- Trees may touch but must not overlap.
- Minimize the metric s^2 / N, where s is the side length of the bounding square.

## Dataset
Kaggle provides the competition files (for example, `sample_submission.csv`). These are not stored in this repository. Place them under a local data folder such as `data/` if you need them for submission formatting.

## Approach
- Model a single tree as a polygon.
- Generate candidate layouts (hex lattice, spiral).
- Compress layouts while maintaining feasibility.
- Polish layouts with small translations and rotations.
- Score layouts using the square side length and select the best candidate per N.

## Repository Structure
- `notebook_final_segmented.ipynb` - primary solver and submission workflow.
- `notebook.ipynb` - exploratory or earlier notebook.
- `LICENSE` - project license.

## Requirements
- Python 3.10+ recommended
- Core libraries: `numpy`, `pandas`, `matplotlib`, `shapely`

Install dependencies:
```bash
python -m venv .venv
.venv\Scripts\activate
pip install numpy pandas matplotlib shapely
```

## Usage
1. Open `notebook_final_segmented.ipynb`.
2. Run the cells to generate layouts and evaluate scores.
3. Build a submission DataFrame and export `submission.csv` if needed.

## Outputs
- `submission.csv` is produced by the notebook when the export cell is enabled.

## Evaluation
The notebook uses:
- `score_state` to compute s^2 / N.
- `rho_state` as an alternate quality measure.
- `has_overlap_state` to validate non-overlap.

## Reproducibility
The current pipeline is deterministic. If you introduce randomness, set a seed and log it in the notebook.

## Notes
- Update `BOUNDS` in the notebook to match the competition's metric notebook.
- The solver focuses on feasibility and compression; further global optimization may improve scores.

## License
See `LICENSE`.
