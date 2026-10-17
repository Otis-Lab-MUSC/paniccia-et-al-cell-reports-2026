# Changelog

All changes in this restructuring, made on branch `chore/restructure-and-readme` relative to `main` (commits `f8fb898` and `e59392e`). For review by Jackie.

## Summary

Reorganized the repository to match the other Otis Lab publication repositories (`martino-et-al-fbn-2026`, `doncheck-et-al-nature-protocols-2026`). **No analysis logic was changed.** The only code edits are to hardcoded data paths, replaced by a single `DATA_ROOT` variable per notebook. The notebooks were not run, because the data are not in the repository.

## Renamed (history preserved with `git mv`)

| Before | After |
|---|---|
| `2026 Paniccia et al_Pav-Imaging-Master_CELL-REPORTS_clean.ipynb` | `notebooks/01_pavlovian_imaging_master.ipynb` |
| `2026 Paniccia et al_Imaging-Behavior.ipynb` | `notebooks/02_imaging_behavior_delta_lickrate_sdt.ipynb` |
| `2026 Paniccia et al_auROC-and-deltaLickrate-to-csv_CBX-analysis.ipynb` | `notebooks/03_cbx_auroc_delta_lickrate.ipynb` |

Names no longer contain spaces and are numbered. Please check the numbering and names suit you.

## Code edits (paths only)

Each notebook gets a new first code cell, `### DATA LOCATION ###`, defining:

```python
DATA_ROOT = os.environ.get('PANICCIA_DATA_ROOT', './data')
```

Hardcoded paths were replaced with `DATA_ROOT`:

| Notebook | Occurrences replaced | Original paths |
|---|---|---|
| 01 | 19 | `C:\Users\Jackie\Dropbox\2P Imaging Projects\Jackie\PFC_GFAP-GCaMP6f_Pavlovian\WholeCell` and `/Users/MAC/Offline/Jackie/WholeCell2 Final` (including commented-out copies) |
| 02 | 3 | `C:\Users\Jackie\Dropbox\Jackie Projects\Projects\2022 PFC_GFAP-LCK-GCaMP6f_Pav-Sucrose\BehaviorData` |
| 03 | 19 | `C:\Users\Jackie\Dropbox\Jackie Projects\Projects\2026 PFC CBX Pavlovian Conditioning\Matlab Files and Codes` and the `...\Reversal` subfolder |

**Please check in notebook 03:** the first analysis cell pointed directly at the `...\Reversal` folder. It is now `os.path.join(DATA_ROOT, 'Reversal')`, so `DATA_ROOT` should be the parent folder (the one holding `Acquisition`, `Reversal` and `Sucrose Omission`). Notebook 01 and 02 behave as before, with `DATA_ROOT` standing in for the old base folder.

Not changed: the `/path/to/averaged_data.pkl` strings in notebook 01 are placeholders inside a printed help message, and one comment mentioning a person's first name. Notebook JSON formatting is unchanged apart from these edits.

## Added

- `README.md`: rewritten in the format of the other publication repositories (overview, notebook table, structure, data, packages, what's not included, citation). The original sentence about Anthropic and OpenAI models is kept. The DOI is a placeholder and will be added later.
- `data/README.md`: the folder layout each notebook expects, read from the notebooks' file-handling code. Please check it against your real folders.
- `requirements.txt`: third-party packages imported by the notebooks. Versions are unpinned.
- `.gitignore`: data files, generated outputs, checkpoints and OS files.
- `CHANGELOG.md`: this file.

## Not added

- No LICENSE, by decision.
- No repository description or topics; those are set on GitHub separately.

## Open items for review

- The README title and overview are my wording; please confirm them or edit them.
- "CBX" is left abbreviated everywhere because its meaning is not stated in the repository.
- The author list, full title and DOI for the Citation section are pending.
