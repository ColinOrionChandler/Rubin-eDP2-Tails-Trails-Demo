# Tails, Trails, and Transients in Rubin eDP2: demo notebooks

Two notebooks that reproduce one example of each science case in the Letter
*Tails, Trails, and Transients: Comets, NEOs, and Supernovae in Rubin Early Data Preview 2*
(Chandler et al., [arXiv:2609.30361](https://arxiv.org/abs/2609.30361)) on the
[Rubin Science Platform](https://data.lsst.cloud).

| Target | Science case | Epoch (UTC date, band) |
| --- | --- | --- |
| C/2024 G6 (ATLAS) | cometary activity | 2025-07-20, *g* |
| 2025 NC₆ | activity on an asteroid-designated object | 2025-07-20, *g* |
| 2025 OP₁ | trailed near-Earth object (≈118 px trail) | 2025-07-23, *g* |
| SN 2025nbh | Type II supernova beside AGC 114905 | 2025-07-22, *r* |

Early Data Preview 2 (eDP2) releases deep coadds, not single-visit images. Where only one or two
visits contributed to a coadd cell, the coadd is effectively a single-epoch image. Both notebooks
find those cells by reading the coadd's per-cell provenance with the Butler, then cut out the
image.

## The notebooks

| Notebook | What it does | Installs | Time |
| --- | --- | --- | --- |
| [`edp2_tails_trails_horizons_demo.ipynb`](edp2_tails_trails_horizons_demo.ipynb) (start here) | Takes a supplied table of visits. It gets times and detectors from the Butler, positions from JPL Horizons, and adds one contrast visit per object that the test rejects | nothing | about 1 minute |
| [`edp2_tails_trails_rsp_demo.ipynb`](edp2_tails_trails_rsp_demo.ipynb) | Finds the epochs from scratch: it predicts the objects in every DP2 visit with Ponder and the Sorcha survey simulator | Ponder and Sorcha, in their own virtual environment under `~/edp2_demo/` | about 15 minutes and 2.5 GB on the first run, about 2 minutes after that |

Both are saved with the outputs of a complete run, so you can read them here without running anything.

## Running them

You need a Rubin Science Platform account with access to eDP2.

1. Open a terminal in the Notebook Aspect at [data.lsst.cloud](https://data.lsst.cloud) and run:
   ```bash
   git clone https://github.com/ColinOrionChandler/Rubin-eDP2-Tails-Trails-Transients-Demo.git
   ```
2. Open a notebook, choose the **LSST** kernel, and run all cells.

Tested on 2026-11-12 with RSP image r30.0.11 (Python 3.13.9). Each notebook checks its own
results and stops with an error if they differ from the Letter.

## Credit

If you use these notebooks, please cite the Letter,
[arXiv:2609.30361](https://arxiv.org/abs/2609.30361). Please also acknowledge Rubin eDP2 data as described on [dp2.lsst.io](https://dp2.lsst.io), JPL
Horizons as described on its [site](https://ssd.jpl.nasa.gov/horizons/), and follow Sorcha's
citation requirements if you use the Ponder notebook.

## Licence

BSD 3-Clause; see [LICENSE](LICENSE).
