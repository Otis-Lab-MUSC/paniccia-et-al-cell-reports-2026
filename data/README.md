# Data

The data are not included in this repository. They are available on request.

Each notebook reads from a single `DATA_ROOT` variable defined in its first code cell. Set it either by editing the default (`./data`) or by setting the `PANICCIA_DATA_ROOT` environment variable. The expected layouts below were taken from the file-handling code in the notebooks.

## `01_pavlovian_imaging_master.ipynb`

```
DATA_ROOT/
├── <day>/<animal>/<fov>/     one folder per imaging day, animal and field of view
│   ├── *.mat                 behavioral event logs (MATLAB)
│   ├── *.npy                 extracted calcium signals
│   └── *RoiSet.zip           ImageJ ROI set for the field of view
├── CellTracking/<tracking_type>/*.csv     cell-tracking tables matching ROIs across days
└── Results/                  written by the notebook
```

The notebook also writes intermediate files (`.npy`, `.pkl`, `.csv`) into the field-of-view folders and into `Results/`.

## `02_imaging_behavior_delta_lickrate_sdt.ipynb`

```
DATA_ROOT/
├── Early/  Late/  SucOmit/  CueOmit/  Rev_Early/  Rev_Late/     behavioral phases, each holding *.mat files
└── Results/                  written by the notebook
```

## `03_cbx_auroc_delta_lickrate.ipynb`

```
DATA_ROOT/
├── Acquisition/<session>/*.mat       sessions are named like PC-D1
├── Reversal/<session>/*.mat          the first analysis cell reads Reversal/<datafolder>, e.g. REV-D20
├── Sucrose Omission/                 omission sessions
└── Results/                          written by the notebook
```
