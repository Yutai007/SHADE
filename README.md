# SHADE: Trace-Based Humanization for Robust and Composable AI-Text Detector Evasion

View the paper at `paper.pdf`.

## SHADE — Reproduction Package (Software)

Code for the experiments reported in the paper.

### Notebook naming

All notebooks live flat in `experiments/`. The filename prefix
indicates its role:

| Prefix | Role |
|---|---|
| (none) | Early exploratory work on context utility U(k) and recurrence frontloading F, before the attack pipeline |
| `C` | Pipeline construction, in numeric order. C02 is the first algorithmic stage; C07 is the complete NS10 pipeline; C08 is the competitor comparison; C09 covers the held-out complement, adaptation and patches |
| `R` | Screening of candidate residual modules against RoBERTa (selected RAFT) |
| `U` | U-adjacent features and their neutralization, run before C07 |
| `F` | F-adjacent feature exploration. **Negative results**: F was found to be directionally heterogeneous and is not used as an attack coordinate. No paper table draws on these |
| `CTRL` | Positive and negative controls |

### Environment

See `requirements/`. Note that each individual experiment could have slightly different requirements, these are specified within the respective notebooks with commented `!pip install ...` cells. All experiments were run on a single NVIDIA RTX 2000 Ada (8 GB).

### Not included

- Adapted detector checkpoints and cached tensors (`.pt`,
  `training_args.bin`). These are regenerable from the attacked
  text and the evaluation notebooks, and derive from
  third-party detectors we do not redistribute.
- The RAID corpus, Ghostbuster's data, and all external data.
  Obtain these from their original sources.

## SHADE — Reproduction Package (Data)

Inputs, outputs and figures for the experiments reported in the paper.

### Layout

- `data/` — cohort definitions, human reference bands, and
  generation inputs. `splits/` holds the 54-source development
  cohort and the disjoint 74-source complement.
- `results/causal/` — one directory per experiment, named for
  the notebook that produced it. Each contains the run records,
  per-text scores and provenance for that experiment.
- `figures/` — figures as they appear in the paper.

### Notes

- Absolute paths in run records have been replaced with
  `REPO_ROOT`.
- Adapted detector checkpoints, cached tensors and `.parquet`
  intermediates are excluded; the same content is available in
  the JSON and CSV records.
- Third-party corpora (RAID, Ghostbuster, etc) are not
  redistributed.
- Most of the data itself can also be regenerated from the inputs and the evaluation notebooks.
