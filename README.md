# Corporate ESG Disclosure and Investment Efficiency in Chinese A-share Firms (2013–2023)

Environmental, Social and Governance (ESG) disclosure is often argued to make
firms more transparent and better governed — but does better disclosure actually
translate into *better capital allocation*? This repository studies whether
higher-quality ESG disclosure improves the **investment efficiency** of Chinese
A-share listed firms over 2013–2023, and whether it does so by reducing the
information asymmetry between firms and their capital providers.

End to end, it turns firm-level financial data, a third-party ESG rating, and
daily market-microstructure data into one clean firm-year panel (**19,103
observations**), constructs an information-transparency measure and three
investment-efficiency measures, and runs the full analysis: year- and
industry-fixed-effects regressions, a lagged mediation model with bootstrap
inference, endogeneity treatment (2SLS and system GMM), and a battery of
heterogeneity and robustness tests.

### Key findings

- **ESG disclosure improves investment efficiency.** Investment efficiency is
  coded as the *negative absolute investment residual* (higher = more efficient),
  so a **positive** ESG coefficient means better efficiency. The ESG-rating
  coefficient is **β = 0.0029 (p < 0.01)** for the most comprehensive measure
  **IE1**, and positive for IE2 (0.0008, p < 0.05) and IE3 (0.0007, p < 0.05)
  with controls. Instrumented (2SLS) estimates are larger and all significant at
  1% (0.0074 / 0.0061 / 0.0060 for IE1 / IE2 / IE3).
- **The channel is information transparency — partial, lagged, and IE1-only.**
  ESG disclosure raises transparency (path *a* = 0.0272, p < 0.01). With a
  **one-year lag**, transparency feeds into IE1 (path *b* = 0.0011, p < 0.01),
  and the bootstrap indirect effect is **0.000030, 95% CI [0.000004, 0.000066],
  p = 0.022** — a significant *partial* mediation for IE1 only. The
  contemporaneous mediation is not detectable, and the channel is insignificant
  for IE2/IE3.
- **Both tails of inefficiency improve.** ESG disclosure constrains both
  **overinvestment** (ESGR_L1 = 0.0030, p < 0.01 for IE1) and **underinvestment**
  (0.0022, p < 0.01 for IE1), with the direct effect somewhat larger in the
  overinvestment subsample. The transparency channel shows up for overinvestment
  via IE1 and for underinvestment via IE2/IE3.
- **Robust to endogeneity treatment.** ESGR is endogenous (Durbin–Wu–Hausman,
  p < 0.01). Using **industry-year, province-year, and industry-province-year
  mean ESG** as instruments (Kleibergen–Paap Wald F = **4,886**), 2SLS confirms a
  positive effect at 1%. Two-step system GMM leaves the ESG coefficient positive
  but insignificant — as expected, since first-differencing absorbs the largely
  *between-firm* variation in ESG ratings, so identification rests on cross-firm
  variation. Results also hold under a **six-agency PCA-based ESG measure**
  (ESGID).
- **The transparency channel is conditional.** It is identified primarily among
  **growth-stage, non-SOE, low-pollution, high-technology, technology-intensive,
  and high-Confucian-culture** firms; the *direct* ESG effect holds broadly
  across these splits.

> This work was completed as an undergraduate Final Year Project (FYP) in
> Accounting at BNBU and is published here for academic-portfolio and
> reproducibility reference. The full assessed thesis is **not** uploaded; this
> repository contains the analysis code, variable construction, and methodology
> summary. Raw data are licensed and are not redistributed (see *Data
> availability*).

## Research questions

1. Does higher-quality ESG disclosure improve corporate investment efficiency?
   *(H1)*
2. Does **information transparency** mediate that relationship? *(H2)*
3. Does ESG disclosure reduce **both overinvestment and underinvestment**? *(H3a/H3b)*

The study additionally maps the *boundary conditions* of the effect across
corporate life-cycle stage, ownership structure, industry characteristics, and
Confucian cultural environment.

## Study design at a glance

- **Unit of analysis:** firm-year.
- **Sample:** Chinese A-share listed firms, **2013–2023**, **N = 19,103**
  observations (lagged-mediation specifications use 15,064; the dynamic GMM uses
  11,943 after lags).
- **Sample screening:** excludes Special Treatment (ST/\*ST) firms, financial-
  industry firms, and observations with missing values; all continuous variables
  are **winsorized at the 1% level**.
- **Identification:** **year + industry fixed effects** as the baseline, with a
  lagged mediation model, 2SLS and two-step system GMM for endogeneity, bootstrap
  mediation, and heterogeneity splits. Standard errors are **clustered at the
  firm level**.

## Data sources

| Source | What it provides | Coverage used |
|---|---|---|
| [Sino-Securities (中证) ESG Rating](https://www.chindices.com) | Third-party ESG rating (AAA–CCC mapped to 9–1), the baseline proxy for ESG disclosure quality (**ESGR**) | 2013–2023 |
| [CSMAR Database](https://data.csmar.com) | Firm-level financial, governance, ownership and market data (controls + investment-model inputs) | 2013–2023 |
| CSMAR **Daily Trading Data** | Daily return/volume used to build liquidity ratio (LR), illiquidity ratio (ILL) and return-reversal gamma (GAM) → the information-transparency measure (**TRANS**) | 2013–2023 |

**Getting the data.** Sino-Securities and CSMAR are licensed databases, typically
available through an institutional subscription. Prepare the input files from
these sources in the format the notebook expects and place them where the
notebook reads them.

## Variables

| Role | Variable | Definition |
|---|---|---|
| Dependent | **IE1** | Negative absolute residual from the Richardson (2006) expected-investment model (the most comprehensive specification) |
| Dependent | **IE2** | Negative absolute residual from the Biddle et al. (2009) model (investment on lagged growth) |
| Dependent | **IE3** | Negative absolute residual from the Chen et al. (2011) model (growth + a negative-growth dummy and its interaction) |
| Independent | **ESGR** | Sino-Securities ESG rating, ordinal 1–9 (CCC→AAA); disclosure-quality proxy |
| Mediator | **TRANS** | Information transparency = **−PC1** of {LR, ILL, GAM}; PC1 explains 73.35% of variance and all three load positively on it, so its negative increases with transparency |
| Controls | Size, PB, Lev, ROA, Altman Z-score (ZS), listing age (LA), board size (Board), independent-director ratio (IDR), average director/executive age (Age), female ratio (Female), financial background (FB), overseas background (OB), largest-shareholder % (TOP), second-shareholder % (SECOND), CEO duality (DUAL), state ownership (SOE) | Firm financial, board, and ownership controls |

> All three IE measures use the **negative** absolute residual, so a higher value
> denotes higher investment efficiency. Full variable construction (the IE1–IE3
> first-stage models and the PCA loadings for TRANS) is documented inside
> `fyp/fyp_analysis_v2.ipynb`.

## Data availability

Raw data are **not** uploaded due to database licensing restrictions. This
repository provides the analysis code, variable definitions, and replication
workflow. Users with access to Sino-Securities and CSMAR can reproduce the
analysis by preparing the corresponding input files.

## Repository structure

```
.
├── README.md
├── LICENSE
├── requirements.txt
└── fyp/
    ├── fyp_analysis_v2.ipynb   # FINAL analysis — use this for all results
    └── fyp_analysis_v1.ipynb   # development notebook — supplementary only
```

`fyp_analysis_v2.ipynb` is the final, authoritative notebook: data processing,
variable construction, descriptive statistics, correlations, the main-effect
regressions, mediation and bootstrap mediation, robustness/endogeneity tests,
and heterogeneity analysis. `fyp_analysis_v1.ipynb` retains preliminary,
development-stage procedures (including some control-variable processing) and is
kept for transparency only — **all reported results refer to v2**.

## Installation

```bash
pip install -r requirements.txt
```

A virtual environment is recommended:

```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Running the analysis

```bash
jupyter notebook fyp/fyp_analysis_v2.ipynb
```

Once the licensed input files are in place, run the notebook top to bottom; it
reproduces every table and figure in order (descriptives → correlations →
main-effect regressions → lagged mediation → robustness/endogeneity →
heterogeneity).

## Methodology

Empirical accounting methods for panel data:

- Descriptive statistics, Pearson correlations, and VIF diagnostics (all VIFs < 3)
- **Baseline regression** of each IE measure on ESGR with controls and year +
  industry fixed effects (H1)
- **Mediation** via the Baron–Kenny (1986) steps plus a **bootstrap** indirect
  effect (1,000 replications), estimated under a one-year lag for both ESGR and
  TRANS (H2)
- **Robustness:** an alternative multi-agency ESG measure (ESGID)
- **Endogeneity:** Durbin–Wu–Hausman test, **2SLS** with three instruments, and
  **two-step system GMM**
- **Heterogeneity analysis** (see below)

## Key modelling and processing decisions

These choices drive how the results should be read:

- **One-year lag on ESGR and TRANS.** The mediation model lags both the ESG
  rating and transparency one year, because disclosure → information environment
  → investment is not instantaneous and contemporaneous transparency/efficiency
  are jointly determined. This lag is *why* the significant mediation appears for
  **IE1** and not contemporaneously.
- **Transparency as −PC1.** TRANS is the negative first principal component of
  the liquidity ratio (LR), illiquidity ratio (ILL) and return-reversal gamma
  (GAM). PC1 loads positively on all three (0.576 / 0.630 / 0.521) and explains
  73.35% of variance, so its negative increases with transparency.
- **Investment efficiency as a residual.** IE1–IE3 are the negative absolute
  residuals from three different expected-investment models (Richardson 2006;
  Biddle et al. 2009; Chen et al. 2011). Because they weight over- and
  under-investment differently, the results are deliberately reported across all
  three, with IE1 as the most comprehensive.
- **Instruments.** ESGR is instrumented with **industry-year (ESG_1),
  province-year (ESG_2), and industry-province-year (ESG_3) mean ESG**. The
  Kleibergen–Paap Wald F = 4,886 rules out weak instruments; over-identification
  tests over-reject in this large sample and are retained following Chen et al.
  (2022).
- **1% winsorization** and exclusion of ST, financial, and missing-value
  observations, to limit outlier and composition distortions.

## Heterogeneity analysis

The direct ESG effect and the transparency channel are examined across:

| Split | Direct ESG effect | Transparency channel (TRANS_L1) |
|---|---|---|
| **Life cycle** (growth/mature/decline) | Significant in all stages | Significant only in **growth-stage** firms (IE1) |
| **Ownership** (SOE vs non-SOE) | Significant for **non-SOEs** only | Significant for **non-SOEs** (IE1) |
| **Pollution** (high vs low) | Stronger in **low-pollution** (1%) than high-pollution (10%) | Significant only in **low-pollution** (IE1) |
| **Technology** (high-tech vs traditional) | Significant in both | Significant only in **high-technology** (IE1) |
| **Factor intensity** (labour/tech/capital) | Broadly significant | **Tech-intensive** (IE1) and **labour-intensive** (IE2/IE3); not capital-intensive |
| **Confucian culture** (high vs low) | Significant in both | Significant only in the **high-Confucian** group (IE1) |

The pattern is consistent throughout: ESG disclosure lifts investment efficiency
broadly, but the *measured transparency channel* is concentrated where the
baseline information environment is weakest or disclosure is most credible.

## Known limitations and caveats

- **Identification is strengthened, not settled.** 2SLS supports a positive
  effect, but ESG ratings are not randomly assigned; the system-GMM ESG
  coefficient is insignificant, so the causal reading rests mainly on cross-firm
  variation rather than within-firm dynamics.
- **Single-agency baseline.** ESGR relies on one rating agency; ratings diverge
  across providers. The six-agency ESGID robustness check mitigates but does not
  eliminate this, since sparse agency coverage required substantial imputation
  and ESGID still partly reflects the dominant rating. Greenwashing may also make
  disclosed ESG deviate from actual practice.
- **Partial, specification-dependent mediation.** The transparency channel is
  *partial*, operates with a one-year lag, and is significant only for **IE1**;
  it should not be generalised across all efficiency measures.
- **External validity.** Evidence is specific to Chinese A-share firms and the
  2013–2023 environment; it may not transfer to other markets or to later
  mandatory-disclosure regimes.
- **Proxy scope.** TRANS is a market-microstructure proxy that captures only part
  of a firm's information environment; textual measures of disclosure quality
  could probe the channel more directly.

## Selected references

Core methodological works (full list in the thesis):

- Richardson, S. (2006). *Over-investment of free cash flow.* Review of
  Accounting Studies, 11(2–3): 159–189.
- Biddle, G. C., Hilary, G., & Verdi, R. S. (2009). *How does financial reporting
  quality relate to investment efficiency?* Journal of Accounting and Economics,
  48(2–3): 112–131.
- Chen, F., Hope, O.-K., Li, Q., & Wang, X. (2011). *Financial reporting quality
  and investment efficiency of private firms in emerging markets.* The Accounting
  Review, 86(4): 1255–1288.
- Amihud, Y. (2002). *Illiquidity and stock returns.* Journal of Financial
  Markets, 5(1): 31–56.
- Pástor, Ľ., & Stambaugh, R. F. (2003). *Liquidity risk and expected stock
  returns.* Journal of Political Economy, 111(3): 642–685.
- Baron, R. M., & Kenny, D. A. (1986). *The moderator–mediator variable
  distinction in social psychological research.* Journal of Personality and
  Social Psychology, 51(6): 1173–1182.

## Author

**Jiayu Hu**
Email: hujiayu211[at]gmail[dot]com
Personal website: [jiayuhu.com](https://www.jiayuhu.com/)

## Supervisor

Assoc. Prof. [Man Hung Alvin Cheng](https://bnbu.edu.cn/en/faculty.htm#/alvinmhcheng/en)
Department of Accounting · Faculty of Business and Management
Beijing Normal–Hong Kong Baptist University (BNBU)

## License

Code in this repository is released under the **MIT License** (see `LICENSE`).
The underlying **Sino-Securities and CSMAR data are proprietary/licensed**, are
**not** covered by that license, and are **not** redistributed here; users must
obtain them from the providers and observe the providers' terms of use. This
repository contains analysis code, variable definitions, and documentation only.
