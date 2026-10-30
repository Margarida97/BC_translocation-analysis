# Bipolar Cell translocation: kinetics analysis

Analysis code for:

> Cruz, M. R., Paixão, T., Coelho, J. and Norden, C. (2026). Birth position and tissue context influence Bipolar Cell translocation mode in the developing retina. *Development*.

## Contents

| File | What it does | Used for |
|---|---|---|
| `instantaneous_velocity.ipynb` | Signed instantaneous velocities, per-cell velocity summary, mean speed, net displacement, path length and average speed | Instantaneous velocity distributions and average speed |
| `pca_kinetics.ipynb` | Five kinetic features per cell, PCA, blind KMeans clustering, PERMANOVA and PERMDISP on aBC vs sBC cohorts, Mann-Whitney tests per PC (Holm-corrected) | Fig. S4 |
| `data/BC_tracks_first100min.csv` | Tracks of 34 apically born (A) and 43 subapically born (S) Bipolar Cells, first 100 min after division | Input for both notebooks; Fig. S4 |

## Input format

A CSV with a `Time` column (min) and one column per cell, holding the position along the apicobasal axis in µm (distance from the apical surface; negative = basal). Missing timepoints can be left empty.

The default CSV format is `;` as separator and `,` as decimal mark. Change `SEP` and `DECIMAL` in the **Config** cell if your file uses `,` and `.`.

For `pca_kinetics.ipynb`, column names must start with `A` (apically born BC) or `S` (subapically born BC), e.g. `A1`, `S12`.

Tracks in the paper were obtained with MTrackJ (Fiji) at 5-min intervals. Directionality Ratios and MSDs reported in the paper were calculated with DiPer (Gorelik and Gautreau, 2014).

## Data

`data/BC_tracks_first100min.csv` holds the position of each cell along the apicobasal axis (µm from the apical surface) every 5 min for the first 100 min after division. Column names: `A1`–`A34` = apically born, `S1`–`S43` = subapically born.

## Installation and use

Requires Python 3.9 or later.

```
pip install -r requirements.txt
jupyter notebook
```

Open a notebook and run all cells. By default both notebooks read `data/BC_tracks_first100min.csv`; to analyse other tracks, set `FILE_PATH` in the **Config** cell. Outputs (CSV tables, and for the PCA the figure as PDF and SVG) are written to the `results/` folder.

## Citation

If you use this code, please cite the paper above and this repository (Zenodo DOI to be added).

## License

MIT
