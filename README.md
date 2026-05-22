# RXCJ2211 Multiple-Image LRD Analysis Code

Analysis notebooks for the Science manuscript:

> **Little red dot variability over a century reveals black hole envelope via a giant Einstein cross**

This repository contains the analysis code used to generate and check the main results, figures, and supporting analyses for the RXCJ2211 multiple-image little red dot (LRD) system.  The code is released to support reproducibility and transparency of the published analysis.

## Repository Contents

| File | Purpose |
| --- | --- |
| `Fig2ab_Fig3abc_FigS10a_lc_fitting.ipynb` | Main light-curve analysis, variability model fitting, parameter-space exploration, and figures corresponding to Fig. 2a,b, Fig. 3a-c, and Fig. S10a.  This notebook also generates the cached `chi2_grid_data.npz` grid. |
| `Fig2c_FigS7_FigS8_check_variability_othersrc.ipynb` | Variability and control-source checks for other lensed sources; used for Fig. 2c, Fig. S7, and Fig. S8. |
| `FigS6_S10_galfitm_sed_RX2lc.ipynb` | GALFITM/photometric SED related checks and RX2 light-curve analysis used for Fig. S6 and Fig. S10. |
| `FigureS2_selection_plot.ipynb` | Selection and comparison plots for the LRD sample, used for Fig. S2. |
| `FigureS4_A.ipynb` | Lensing magnification/source-plane calculations, including the VENUS magnification-calculator workflow used for Fig. S4A. |
| `cluster_photz_distribution.ipynb` | EAZY photometric-redshift probability distributions for the cluster/lensed sources. |
| `check_lensmodel_systematics.ipynb` | Lens-model systematic checks, including comparisons among alternative lens models, magnification and time-delay tables, and propagation into light-curve/SED quantities. |
| `lc_fitting_chemamodel.ipynb` | Repeat light-curve fitting with the Chema/Diego Case2 lens model and comparison against the fiducial Oguri model. |
| `lc_fitting_othersources.ipynb` | Light-curve fitting for other sources used as consistency/control checks. |
| `check_z6magnification.ipynb` | Redshift and magnification robustness checks, including tests at higher source redshift. |
| `chi2_grid_data.npz` | Cached chi-square grid used by the light-curve parameter-space plots. |

The manuscript PDF `RXCJ2211_MILRDs__Science__.pdf` is included here only as a local reference copy.  Please cite the published paper once the final bibliographic information is available.

## Data

The notebooks rely on imaging, catalog, EAZY, lens-model, and intermediate products described in the paper.  In the working analysis tree these inputs were organized next to `analysis_code/`, for example:

```text
RXCJ2211/
  analysis_code/
  catalog/
  EAZY_v01/
  HST_image/
  imaging_data/
  lensing_model/
  relic_lens_model/
  sfw_image/
  Cepheids_L_T/
  figure/
```

Some notebooks still contain absolute paths from the original analysis environment, e.g. `/Users/zijianzhang/Astro_Data/multi-image_LRD_cluster/RXCJ2211/...`.  To rerun the notebooks on another machine, either reproduce the directory layout above or update the path variables near the top of each notebook.

Large observational data products are not duplicated in this code-only release.  They should be obtained from the public archives and/or the paper's Data Availability statement.  Derived tables or intermediate products that are needed for exact reproduction should be placed in the corresponding folders listed above.

## Software Requirements

The notebooks were developed primarily in Python/Jupyter environments named `msaexp39` and `jwstpy311_new`.  A typical environment should include:

```bash
conda create -n rxcj2211-analysis python=3.11
conda activate rxcj2211-analysis
pip install numpy scipy pandas matplotlib astropy photutils h5py pyyaml tqdm joblib emcee extinction sep loess
pip install eazy grizli msaexp
```

Depending on the notebook being run, additional packages may be required, including `dust_attenuation`, `statmorph`, `galsim`, and local analysis helpers used in the original full analysis tree.  For `dust_attenuation`, the notebooks expect the Karl Gordon package:

```bash
pip install git+https://github.com/karllark/dust_attenuation.git
```

Exact package versions were not frozen in the exploratory notebooks.  For publication reproduction, record the environment used to rerun the notebooks with:

```bash
python -m pip freeze > requirements-reproduced.txt
```

## Suggested Reproduction Order

The notebooks are figure-oriented and can be run independently once their input data are available.  A practical order is:

1. `cluster_photz_distribution.ipynb` and `FigureS2_selection_plot.ipynb` for photometric-redshift and sample-selection diagnostics.
2. `FigureS4_A.ipynb` and `check_lensmodel_systematics.ipynb` for lensing magnification, source-plane, and time-delay quantities.
3. `Fig2ab_Fig3abc_FigS10a_lc_fitting.ipynb` for the fiducial light-curve analysis and main parameter-space results.
4. `lc_fitting_chemamodel.ipynb`, `check_z6magnification.ipynb`, and `lc_fitting_othersources.ipynb` for robustness and alternative-assumption checks.
5. `Fig2c_FigS7_FigS8_check_variability_othersrc.ipynb` and `FigS6_S10_galfitm_sed_RX2lc.ipynb` for additional figure panels and supporting checks.

Most figures are written to the sibling `figure/` directory in the original analysis tree.

## Notes on Reproducibility

- These notebooks are the research notebooks used for the paper analysis, not a packaged Python library.
- Several cells are designed for interactive inspection and may include diagnostic outputs from exploratory runs.
- Some notebooks contain hard-coded absolute paths; edit the path definitions before running in a new environment.
- The lensing notebooks require the corresponding lens-model FITS maps and YAML/table inputs.
- The EAZY notebooks require the EAZY `.h5`, catalog, template, filter, and template-error files used in the paper.
- The cached `chi2_grid_data.npz` is provided so that the corresponding parameter-space figure can be regenerated without rerunning the full grid search.

## Citation

If you use this code, please cite:

```text
Zhang et al., "Little red dot variability over a century reveals black hole envelope via a giant Einstein cross", Science, in press/submitted.
DOI: [add DOI after publication]
Code archive: [add GitHub/Zenodo URL]
```

## License

Add the intended license before public release, for example `MIT`, `BSD-3-Clause`, or the license required by the journal/collaboration.

