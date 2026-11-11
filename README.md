# Planar KDE persistence: reproducibility archive

This is the code and saved-results archive for Jiaxuan Ren, *Limit laws for shallow loops in planar Gaussian kernel density estimates*. Preparing this archive did not generate new samples, KDEs or persistence computations.

The archive covers the two studies in Section 7 of the first paper. It does not contain the second paper, correspondence, internal handoffs or manuscript files.

| Study | Saved observations | Main numerical statistic | Paper displays |
|---|---:|---|---|
| Gaussian-difference model | 3,200 repetitions; 8 cells × 400 | Rescaled longest mode-6 PL bar after the predeclared numerical noise floor | Figures 3–4 and paired-error table |
| Circular angular designs | 2,400 repetitions; 12 cells × 200 | Rescaled raw longest positive mode-6 PL bar; all positive bars retained | Figure 5 |

## Obtain the complete bundle

For a browser download, obtain these three files from this repository:

1. `planar-kde-persistence-source.zip` — extract this source-and-summary bundle.
2. `gaussian_difference_records.zip` — place this unchanged ZIP in the extracted `data/` directory.
3. `angular_design_records.zip` — place this unchanged ZIP in that same `data/` directory.

Run commands from the extracted directory containing this README, `tools/`, `data/`, and `experiments/`. A checkout that already contains the two record ZIPs needs no separate downloads. The record ZIPs are each below the browser upload limit; keep their names unchanged. All commands below use relative paths.

The two ZIP files inside `data/` are compact **saved JSON records**, not another source checkout. They include every planned repetition and all saved per-row error-budget information. No observations were selected for this release.

## Verify or recompute saved results

Python 3.12 or newer is recommended for this convenience analysis layer. Install the versions in `requirements.txt` in your own environment. These are the saved-data analysis dependencies, not a claim that the two original simulations used identical environments.

```bash
python -m venv .venv
# Activate .venv using the command for your operating system.
python -m pip install -r requirements.txt
python tools/verify_manifest.py
python tools/recompute_saved.py --experiment gaussian_difference --output work/gaussian-analysis
python tools/recompute_saved.py --experiment angular_design --output work/angular-analysis
```

Each output directory must be new. The commands check the complete identity/seed sets and recompute the archived numerical tables using unchanged analysis functions. They do **not** draw data, evaluate a KDE, calculate persistent homology, or verify the omitted raw arrays. A `RECOMPUTATION.json` records agreement with the saved summaries, allowing small floating-point library differences.

Add `--plots` to either recomputation command to recreate the corresponding historical plots from saved records. The revised portrait plots used in the current presentation can be created independently:

```bash
python tools/plot_portrait.py --input data/plot_data.json --out-dir work/portrait-figures
```

`plot_data.json` contains all plotted observations, paired values, and the evaluated analytic curves. To reconstruct that compact plot input directly from the unchanged Gaussian-difference records:

```bash
python tools/extract_saved_records.py --experiment gaussian_difference --output work/gaussian-records
python tools/export_plot_data.py --run-dir work/gaussian-records --code-dir experiments/gaussian_difference/frozen_code --out-dir work/plot-data
```

The extraction command also restores both original analysis JSON files and both original PNGs required by the plot export binding. The final two plotting scripts are presentation tools. The frozen scientific calculation and original saved tables remain separately preserved.

## Frozen design, seeds and scientific source

- `experiments/gaussian_difference/frozen_code/` contains distribution copies of all 22 files bound by the historical source freeze. The design uses `q=0.5`, `H=0.25`, `n={10000,100000}`, `s={-1,0,1,2}`, and 400 repetitions per cell. Seed: `20261110000000 + 10000*cell + rep`.
- `experiments/angular_design/frozen_code/` contains distribution copies of the seven frozen science files and the storage/analysis functions. `frozen_reference/` retains the exact design and formal plan. There are three angular laws, two sample sizes and two fixed local parameters. Seed: `20261105800000 + 1000*cell + rep`, `rep=0,...,199`.
- The design documents retain their historical `CANDIDATE` labels. The later freeze metadata record the original snapshots before the saved run. This is a locally recorded freeze, **not externally timestamped preregistration**. The angular formal plan and science payload specify the final half-spacing grid; the earlier `grid_initial` string alone is not the executed design.
- Source annotations and administrative metadata have been normalized for this distribution; numerical algorithms, seeds, designs, and saved values are unchanged. `FILE_MANIFEST.json` binds the current distributed files. Historical hashes in freeze metadata refer to the separately retained original snapshots, not to edited distribution copies. See `PROVENANCE.md` and `PROVENANCE.json`.

## Running new simulations is a separate operation

The commands above never start a simulation. New simulation runs may take hours and need a separate output directory, environment record and new run identity.

For the Gaussian-difference experiment, the original entry points are `frozen_code/scripts/make_freeze.py`, `run_candidate.py`, `verify_run.py`, and `analyze_candidate.py`. Their original environment and explicit freeze/authorization gates remain intact. Read the docstrings and the archived `ENV_LOCK.json` before using them. The historical numerical allowances were calibrated on Apple Accelerate, Python 3.13.0, NumPy 2.5.4 and SciPy 1.18.1; the original guard may correctly refuse another environment. `requirements.lock` is a historical record, not a directly installable pip requirements file because it also records Python and compiler information.

For angular designs, `science82.sample` and `science82.compute` are the unchanged scientific entry points; `records82.design` reads the frozen design. The historical Mac launcher depended on private machine paths and internal run-control files and is not presented as a portable command. A full new run requires a launcher that binds the supplied design, uses the stated seed order, retains every result/failure, and records its environment. The archive therefore supports **complete saved-result reproduction now**, while full scientific reruns retain their original environment/launcher requirements. No portability or exact floating-point replay across systems is claimed.

## Numerical interpretation and limits

The saved statistics are finite-resolution numerical bars. A numerical zero does not certify absence of a bar of the continuous KDE on the whole plane.

For the Gaussian-difference study, the error budgets are empirical/conditional, including rounding allowances measured in the historical environment. They provide sensitivity analysis, not certified confidence statements about the continuous statistic. The angular interpolation bounds concern the finite Fourier field only; KDE-to-Fourier and floating-point evaluation errors remain outside that bound. Clopper–Pearson intervals describe the specified numerical indicators.

The studies are finite-sample illustrations for fixed parameter choices. They do not establish a convergence rate, a uniformly calibrated test, or performance on biological observations. All sample sizes, zero values, discrepancies and declared denominators are retained.

## Files omitted from this compact archive

The angular run's 12,000 NPZ files (about 3.55 GB) are not included. Original JSON records retain array shapes, hashes, sample RNG states and interpolation calculations, but those hashes cannot be reverified against omitted bytes from this bundle alone. Gaussian-difference sample arrays were not saved; the original seeds and source are supplied. No third-party libraries, compiled binaries or credentials are bundled.
