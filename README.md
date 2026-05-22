# RXCJ2211 Multiple-Image LRD Analysis Code

Analysis notebooks for the Science manuscript:

> **Little red dot variability over a century reveals black hole envelope via a giant Einstein cross**

This repository contains the analysis code used to generate and check the main results, figures, and supporting analyses for the RXCJ2211 multiple-image little red dot (LRD) system.  The code is released to support reproducibility and transparency of the published analysis.

## Repository Contents

| File | Purpose |
| --- | --- |
| `Fig2ab_Fig3abc_FigS10a_lc_fitting.ipynb` | Main light-curve analysis, variability model fitting, parameter-space exploration, and figures corresponding to Fig. 2a,b, Fig. 3a-c, and Fig. S10a for RX1.  This notebook also generates the cached `chi2_grid_data.npz` grid. |
| `Fig2c_FigS7_FigS8_check_variability_othersrc.ipynb` | Variability and control-source checks for other lensed sources; used for Fig. 2c, Fig. S7, and Fig. S8. |
| `FigS6_S10_galfitm_sed_RX2lc.ipynb` | GALFITM/photometric SED related checks and RX2 light-curve analysis used for Fig. S6 and Fig. S10. |
| `FigS2_selection_plot.ipynb` | Selection and comparison plots for the LRD sample, used for Fig. S2. |
| `cluster_photz_distribution.ipynb` | EAZY photometric-redshift probability distributions for the cluster/lensed sources. |
| `check_lensmodel_systematics.ipynb` | Lens-model systematic checks, including comparisons among alternative lens models, magnification and time-delay tables, and propagation into light-curve/SED quantities. |
| `lc_fitting_chemamodel.ipynb` | Repeat light-curve fitting with the Chema/Diego Case2 lens model and comparison against the fiducial Oguri model. |
| `lc_othersources.ipynb` | Light-curve fitting for other sources used as consistency/control checks. |
| `check_z6magnification.ipynb` | Redshift and magnification robustness checks, including tests at higher source redshift. |
| `chi2_grid_data.npz` | Cached chi-square grid used by the light-curve parameter-space plots. |

## Data

The notebooks rely on imaging, catalog, EAZY, lens-model, and intermediate products described in the paper.  In the working analysis tree these inputs were organized next to `analysis_code/`, for example:

```text
RXJ2211_LensedLRD/
  analysis_code/
  catalog/
  lensing_model/
```

Some notebooks still contain absolute paths from the original analysis environment.  To rerun the notebooks on another machine, either reproduce the directory layout above or update the path variables near the top of each notebook.

Large observational data products are not duplicated in this code-only release.  They should be obtained from the public archives and/or the paper's Data Availability statement.  Derived tables or intermediate products that are needed for exact reproduction are placed in the corresponding folders listed above.

## Software Requirements

The notebooks were developed primarily in Python/Jupyter environments.  A typical environment should include:

```bash
conda create -n rxcj2211-analysis python=3.11
conda activate rxcj2211-analysis
pip install numpy scipy pandas matplotlib astropy photutils h5py pyyaml tqdm joblib emcee extinction sep loess
```

## Notes on Reproducibility

- These notebooks are the research notebooks used for the paper analysis, not a packaged Python library.
- Several cells are designed for interactive inspection and may include diagnostic outputs from exploratory runs.
- Some notebooks contain hard-coded absolute paths; edit the path definitions before running in a new environment.
- The lensing notebooks require the corresponding lens-model FITS maps and YAML/table inputs. The map of the fiducial galfic model can be retrived from https://zenodo.org/records/20312327.
- The EAZY notebooks require the EAZY `.h5`, catalog, template, filter, and template-error files used in the paper.
- The cached `chi2_grid_data.npz` is provided so that the corresponding parameter-space figure can be regenerated without rerunning the full grid search.

## Citation

If you use this code, please cite:

```text
@ARTICLE{2025arXiv251205180Z,
       author = {{Zhang}, Zijian and {Li}, Mingyu and {Oguri}, Masamune and {Lin}, Xiaojing and {Inayoshi}, Kohei and {Cerny}, Catherine and {Coe}, Dan and {Diego}, Jose M. and {Fujimoto}, Seiji and {Jiang}, Linhua and {Mahler}, Guillaume and {Matthee}, Jorryt and {Naidu}, Rohan P. and {Sharon}, Keren and {Shen}, Yue and {Zitrin}, Adi and {Abdurro'uf} and {Akins}, Hollis and {Allingham}, Joseph F.~V. and {Amor{\'\i}n}, Ricardo and {Asada}, Yoshihisa and {Atek}, Hakim and {Bauer}, Franz E. and {Brada{\v{c}}}, Maru{\v{s}}a and {Bradley}, Larry D. and {Cai}, Zheng and {Cantalupo}, Sebastiano and {Conselice}, Christopher and {Dai}, Liang and {Dayal}, Pratika and {Egami}, Eiichi and {Eisenstein}, Daniel J. and {Faisst}, Andreas L. and {Fan}, Xiaohui and {Fei}, Qinyue and {Frye}, Brenda L. and {Fudamoto}, Yoshinobu and {Furtak}, Lukas J. and {Golubchik}, Miriam and {Gonz{\'a}lez-Otero}, Mauro and {Harikane}, Yuichi and {Hsiao}, Tiger Yu-Yang and {Jim{\'e}nez-Teja}, Yolanda and {Kartaltepe}, Jeyhan S. and {Kiyota}, Tomokazu and {Koekemoer}, Anton M. and {Kohno}, Kotaro and {Kokorev}, Vasily and {Kumari}, Nimisha and {Labbe}, Ivo and {Lagos}, Claudia D.~P. and {Larison}, Conor and {Liang}, Yongming and {Lucas}, Ray A. and {Lyu}, Jianwei and {Martis}, Nicholas S. and {Magdis}, Georgios E. and {Messa}, Matteo and {Nakane}, Minami and {Noirot}, Ga{\"e}l and {Ortiz}, III, Rafael and {Ouchi}, Masami and {Pierel}, Justin D.~R. and {Postman}, Marc and {Reddy}, Naveen and {Ricotti}, Massimo and {Schaerer}, Daniel and {Schneider}, Raffaella and {Steidel}, Charles C. and {Tee}, Wei Leong and {Tripodi}, Roberta and {Trussler}, James A.~A. and {Umeda}, Hiroya and {Valentino}, Francesco and {Vanzella}, Eros and {Wang}, Feige and {Windhorst}, Rogier and {Wu}, Yunjing and {Wu}, Zihao and {Yanagisawa}, Hiroto and {Yang}, Jinyi and {Sun}, Fengwu},
        title = "{Little red dot variability over a century reveals black hole envelope via a giant Einstein cross}",
      journal = {arXiv e-prints},
     keywords = {Astrophysics of Galaxies},
         year = 2025,
        month = dec,
          eid = {arXiv:2512.05180},
        pages = {arXiv:2512.05180},
          doi = {10.48550/arXiv.2512.05180},
archivePrefix = {arXiv},
       eprint = {2512.05180},
 primaryClass = {astro-ph.GA},
       adsurl = {https://ui.adsabs.harvard.edu/abs/2025arXiv251205180Z},
      adsnote = {Provided by the SAO/NASA Astrophysics Data System}
}
```

