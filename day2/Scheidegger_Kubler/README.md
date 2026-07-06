# Day 2 — Deep Equilibrium Nets

Simon Scheidegger

Six sessions: an introduction to Deep Equilibrium Nets (theory), a session on
tuning them (architecture search and loss balancing), a primer on automatic
differentiation for DEQNs, two applications (IRBC and OLG), and a climate-economics
session (DICE/CDICE integrated assessment models).

## Agenda mapping (Tue, July 7)

Per the [school agenda](https://liboecon.com/2026_summer_school_agenda.html):

- **Lecture 4** (9:00–10:30) *Deep Equilibrium Nets: Foundations* — Session 1 (Brock–Mirman).
- **Lecture 5** (11:00–12:30) *Deep Equilibrium Nets: Applications* — Sessions 4–5 (IRBC, OLG).
- **Tutorial 2** (14:00–15:30) *Hands-on Practice* — the exercise notebooks, plus Session 2 (NAS & loss normalization).
- **Self-study:** this folder deliberately contains more than the slots can cover — the full Session-2 decks (NAS, loss normalization), the automatic-differentiation primer (Session 3), the climate-economics session (Session 6), the loss-kernel comparison notebook, the exercises with solutions, and the lecture script in `readings/`.

| Session | Topic | Slides | Notebooks |
|---|---|---|---|
| 1 | Deep Equilibrium Nets: theory & Brock–Mirman | [`slides/01_brock_mirman/01_deep_equilibrium_nets.tex`](slides/01_brock_mirman/) | [`code/01_brock_mirman/`](code/01_brock_mirman/) |
| 2 | Neural architecture search & loss normalization | [`slides/02_nas_loss_normalization/`](slides/02_nas_loss_normalization/) (two decks: `02_01` NAS, `02_02` loss normalization) | [`code/02_nas_loss_normalization/`](code/02_nas_loss_normalization/) |
| 3 | Automatic differentiation for DEQNs | [`slides/03_autodiff_for_deqns/03_autodiff_for_deqns.tex`](slides/03_autodiff_for_deqns/) | [`code/03_autodiff_for_deqns/`](code/03_autodiff_for_deqns/) |
| 4 | Application: International Real Business Cycles (IRBC) | [`slides/04_irbc/04_irbc.tex`](slides/04_irbc/) | [`code/04_irbc/`](code/04_irbc/) |
| 5 | Application: Overlapping Generations (OLG) | [`slides/05_olg/05_olg_models_deqns.tex`](slides/05_olg/) | [`code/05_olg/`](code/05_olg/) |
| 6 | Climate economics: DICE/CDICE integrated assessment models | [`slides/06_climate/06_climate.tex`](slides/06_climate/) | [`code/06_climate/`](code/06_climate/) |

## Notebooks

To run locally: `pip install -r requirements.txt` (see [`requirements.txt`](requirements.txt); Python 3.10–3.12, TensorFlow-based).

**Session 1 — Brock–Mirman** (`code/01_brock_mirman/`)

- `01_01_Brock_Mirman_1972_DEQN.ipynb` — deterministic Brock–Mirman, uniform sampling
- `01_02_Brock_Mirman_Uncertainty_DEQN.ipynb` — stochastic Brock–Mirman, simulation-based sampling
- `01_03_DEQN_Exercises_Blanks.ipynb` — **exercise** (KKT + Fischer–Burmeister, 6-period OLG), blank template
- `01_04_DEQN_Exercises_Solutions.ipynb` — exercise solutions
- `01_05_StochasticBM_LossComparison.ipynb` — loss-kernel comparison (MSE, LogCosh, Huber, …)

**Session 2 — NAS & loss normalization** (`code/02_nas_loss_normalization/`)

- `02_01_NAS_Random_Search_10D.ipynb` — random search on a 10-D testbed
- `02_02_NAS_RandomSearch_Hyperband.ipynb` — random search vs. successive halving
- `02_03_Loss_Normalization.ipynb` — equal / inverse-loss / ReLoBRaLo weighting

**Session 3 — Automatic differentiation for DEQNs** (`code/03_autodiff_for_deqns/`)

- `03_01_AutoDiff_Analytical_Examples.ipynb` — three ways to differentiate; forward/reverse modes; 2-D gradient fields
- `03_02_Brock_Mirman_AutoDiff_DEQN.ipynb` — deterministic Brock–Mirman via the autodiff Euler residual
- `03_03_Brock_Mirman_Uncertainty_AutoDiff_DEQN.ipynb` — stochastic Brock–Mirman + Gauss–Hermite quadrature
- `03_04_IRBC_AutoDiff_DEQN.ipynb` — IRBC under the autodiff template (**self-study** extension)

**Session 4 — IRBC** (`code/04_irbc/`)

- `04_01_IRBC_DEQN_smooth.ipynb` — smooth benchmark, in-class walk-through
- `04_02_IRBC_DEQN_irreversible.ipynb` — irreversible investment (Fischer–Burmeister)
- `04_03_IRBC_Exercise.ipynb` — **exercise** (comparative statics + inverse-loss weighting)

**Session 5 — OLG** (`code/05_olg/`)

- `05_01_OLG_Analytic_DEQN_exogenous.ipynb` — analytic 6-agent model, exogenous sampling
- `05_02_OLG_Analytic_DEQN_persistent.ipynb` — analytic 6-agent model, persistent simulation (primary)
- `05_03_OLG_Benchmark_DEQN_exogenous.ipynb` — 56-cohort AGS benchmark, exogenous sampling
- `05_04_OLG_Benchmark_DEQN_persistent.ipynb` — 56-cohort AGS benchmark, persistent simulation (primary)
- `05_05_OLG_Exercise.ipynb` — **exercise** (closed-form savings rates, lifecycle profiles)

**Session 6 — Climate economics (DICE/CDICE)** (`code/06_climate/`)

- `06_01_Climate_Exercise.ipynb` — **exercise** (pure NumPy warm-up: three-box carbon cycle, temperature layer, quadratic damages, BAU vs. abatement)
- `06_02_DICE_DEQN_Library_Port.ipynb` — deterministic CDICE solved with a DEQN (self-contained port of the production library)
- `06_03_Stochastic_DICE_DEQN.ipynb` — stochastic CDICE-DEQN, AR(1) productivity shock + Gauss–Hermite quadrature (**self-study** extension)

The tuned, production-grade code behind this session lives at
<https://github.com/ClimateChangeEcon/Climate_in_Climate_Economics>.

## Readings

See [`readings/`](readings/):

- **Lecture script (book):** [`Deep_Learning_for_Solving_And_Estimating_Dynamic_Economic_Models.pdf`](readings/Deep_Learning_for_Solving_And_Estimating_Dynamic_Economic_Models.pdf) — the chapter references in the slides and notebooks (Ch. 2 Brock–Mirman, Ch. 3 IRBC, Ch. 4 NAS/loss balancing, Ch. 5 OLG) point to this script.
- Azinovic, Gaegauf & Scheidegger (2022, *IER*) — the DEQN paper.
- Deep-UQ and optimal-taxation companion papers.
- Folini, Friedl, Kübler & Scheidegger (2025, *ReStud*) — [`Climate_in_Climate_Econ.pdf`](readings/Climate_in_Climate_Econ.pdf); the CDICE model behind Session 6.

## Further material

These lectures are a condensed selection. The full library — many more lectures, notebooks,
and the always-current version of the script — lives at
<https://github.com/sischei/Deep_Learning_for_Solving_And_Estimating_Dynamic_Economic_Models>.

## Notation conventions

Across all day-2 decks: network parameters are **θ** (policy network 𝒩_θ), the
training loss is **ℓ_θ**, and economic symbols follow the lecture script (α capital
share, β discount factor, ϱ/ρ_z TFP persistence). ReLoBRaLo's balancing
hyperparameters (T, α, ρ) in Session 2 follow the loss-balancing literature and
are unrelated to the economic symbols.
