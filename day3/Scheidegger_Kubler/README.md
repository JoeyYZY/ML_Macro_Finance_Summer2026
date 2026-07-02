# Day 3 — Surrogates, Structural Estimation & Optimal Policy

Simon Scheidegger · Felix Kübler

Three sessions that build on Day 2's Deep Equilibrium Nets: what surrogate
models are and how they are used in economics and finance, structural
estimation with simulated method of moments (SMM) on a surrogate, and
constrained optimal carbon taxation as a surrogate application (with
uncertainty quantification of the social cost of carbon in the appendix).

| Session | Topic | Slides | Notebooks |
|---|---|---|---|
| 1 | Surrogate models in economics & finance (GP toolbox in the appendix) | [`slides/01_surrogates_and_gps/01_surrogates.tex`](slides/01_surrogates_and_gps/) | [`code/01_surrogates_and_gps/`](code/01_surrogates_and_gps/) |
| 2 | Structural estimation with SMM | [`slides/02_structural_estimation_smm/02_smm.tex`](slides/02_structural_estimation_smm/) | [`code/02_structural_estimation_smm/`](code/02_structural_estimation_smm/) |
| 3 | Optimal carbon taxes with deep surrogates (appendix: UQ of the SCC) | [`slides/03_optimal_tax/03_optimal_tax_surrogates.tex`](slides/03_optimal_tax/) | — (paper-based session) |

## Notebooks

To run locally: `pip install -r requirements.txt` (see [`requirements.txt`](requirements.txt); Python 3.10–3.12, PyTorch/scikit-learn-based).

**Session 1 — Surrogates & the GP toolbox** (`code/01_surrogates_and_gps/`)

- `01_01_Surrogate_Primer.ipynb` — Black–Scholes deep surrogate with implied-volatility inversion (main part)
- `01_02_GP_and_BAL.ipynb` — GP regression from scratch + Bayesian active learning (appendix A/B)
- `01_03_GP_Value_Function_Iteration.ipynb` — GP-based value-function iteration (appendix C)
- `01_04_Active_Subspace_2D.ipynb`, `01_05_Active_Subspace_10D.ipynb`, `01_06_Active_Subspace_Nonlinear.ipynb` — active subspaces (appendix C)
- `01_07_Deep_Kernel_Learning.ipynb` — neural feature maps + GP uncertainty (appendix A)
- `01_08_Deep_Active_Subspace_Ridge.ipynb` / `01_09_Deep_AS_vs_Linear_AS_Borehole.ipynb` — deep vs. linear active subspaces (appendix C)

**Session 2 — SMM** (`code/02_structural_estimation_smm/`)

- `02_01_Structural_Estimation_BM.ipynb` — scalar SMM: estimate the TFP persistence ϱ
- `02_02_Structural_Estimation_BM_Joint.ipynb` — joint (β, ϱ) estimation and the identification ridge

**Session 3** has no notebooks; the deck is based on Friedl, Kübler, Scheidegger &
Usui (2023, deep UQ) and Kübler, Scheidegger & Surbek (2026, constrained optimal
carbon taxes).

## Notation conventions

Day 3 works in an estimation/policy setting, so — unlike Day 2 — **θ denotes
structural parameters** (and ϑ policy parameters). Network weights are written
**ρ** where they appear explicitly (Session 3 appendix); the training loss is ℓ.
The Session-1 lazy-learning frames follow the same convention.

## Readings

- The **lecture script** (chapters on surrogates, SMM ≈ Ch. 9–10) is in
  [`../../day2/Scheidegger_Kubler/readings/`](../../day2/Scheidegger_Kubler/readings/).
- Much more material — additional lectures, notebooks, and the always-current
  script — in the library:
  <https://github.com/sischei/Deep_Learning_for_Solving_And_Estimating_Dynamic_Economic_Models>.
