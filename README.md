# The Impact of Corporate Environmental, Social and Governance (ESG) Disclosure on Corporate Investment Efficiency

## Short Description

This accounting empirical research project examines the impact of corporate Environmental, Social, and Governance (ESG) disclosure on investment efficiency among Chinese A-share listed firms from 2013 to 2023. By using firm-level financial data, ESG rating data, and information transparency measures, this study investigates whether higher-quality ESG disclosure improves corporate investment efficiency by reducing information asymmetry and mitigating overinvestment and underinvestment. Through fixed-effects regression, mediation analysis, robustness tests, instrumental variable estimation, and heterogeneity analysis, the project provides empirical accounting evidence on how ESG disclosure contributes to sustainable corporate governance, efficient capital allocation, and evidence-based policymaking.

### Author

Jiayu Hu

Email: hujiayu211[at]gmail[dot]com

Personal website:

Undergraduated Thesis:<br>[BBA in Accounting](https://fbm.bnbu.edu.cn/acct_en/)<br>[Faculty of Business and Management](https://fbm.bnbu.edu.cn/en/)<br>[Beijing Normal Hong Kong Baptist University](https://www.bnbu.edu.cn/en/)

## Purpose

This project explores the relationship between ESG disclosure and corporate investment efficiency in the context of China’s capital market. It aims to understand whether ESG disclosure can serve as an effective information mechanism that improves corporate transparency, reduces agency problems, and helps firms make more efficient investment decisions.

Specifically, this project focuses on three main research questions:

1. Whether ESG disclosure has a positive impact on corporate investment efficiency.
2. Whether information transparency mediates the relationship between ESG disclosure and investment efficiency.
3. Whether ESG disclosure helps reduce both overinvestment and underinvestment.

The study also examines whether this relationship differs across corporate life cycle stages, ownership structures, industry characteristics, and Confucian cultural environments.

## Data Source and Collection Method

The project uses data from Chinese A-share listed firms from 2013 to 2023. The sample excludes Special Treatment firms, financial firms, and observations with missing values. Continuous variables are winsorized at the 1% level to reduce the influence of outliers.

The main data sources include:

- [Sino-Securities Index](https://www.chindices.com): Used to collect ESG rating data as a proxy for ESG disclosure quality.
- [CSMAR Database](https://data.csmar.com): Used to collect firm-level financial, governance, ownership, and market data.
- Daily Trading Data (from [CSMAR](https://data.csmar.com)): Used to construct information transparency measures based on liquidity and information asymmetry indicators.

The key variables include:

- Dependent Variable: Investment efficiency, measured using residual-based models.
- Independent Variable: ESG disclosure, proxied by ESG rating scores.
- Mediating Variable: Information transparency, constructed from market microstructure indicators using principal component analysis.
- Control Variables: Firm size, leverage, return on assets, price-to-book ratio, Z-score, listing age, board characteristics, ownership structure, CEO duality, and state ownership.

## Methodology

This project applies empirical accounting research methods to examine the relationship between ESG disclosure and investment efficiency.

The main methods include:

- Descriptive statistics
- Pearson correlation analysis
- Fixed-effects regression
- Mediation effect testing
- Bootstrap mediation analysis
- Robustness tests using alternative ESG disclosure measures
- Instrumental variable estimation
- Two-stage least squares regression
- Generalized Method of Moments estimation
- Heterogeneity analysis

The heterogeneity tests cover:

- Corporate life cycle
- Overinvestment and underinvestment
- State-owned and non-state-owned enterprises
- High-pollution and low-pollution industries
- High-technology and traditional industries
- Labor-intensive, technology-intensive and capital-intensive industries
- Confucian cultural influence

## Installation and Usage

Install the required dependencies as follows:

```bash
pip install -r requirements.txt
```

The `requirements.txt` file contains the Python packages used for data processing, econometric analysis, and result generation.

### Analyzing the Empirical Results

Run the final empirical analysis notebook with:

```bash
jupyter notebook fyp_analysis_v2.ipynb
```

The `fyp_analysis_v2.ipynb` notebook is the final version used for the main empirical analysis. It includes data processing, variable construction, descriptive statistics, correlation analysis, fixed-effects regressions, mediation tests, robustness checks, endogeneity tests, and heterogeneity analysis.

For transparency and reproducibility, an earlier development notebook is also included:

```bash
jupyter notebook fyp_analysis_v1.ipynb
```

The `fyp_analysis_v1.ipynb` notebook contains preliminary testing and development-stage procedures, including the processing of control variables used in the main-effect regressions. This file is retained as supplementary documentation only. The final results and interpretations should refer to `fyp_analysis_v2.ipynb`.

## Project Outcomes

The insights derived from this study provide stakeholders with a better understanding of how ESG disclosure influences corporate investment efficiency in China’s capital market. The empirical results show that higher-quality ESG disclosure can improve information transparency, reduce information asymmetry, and help firms alleviate overinvestment and underinvestment.

These findings contribute to the accounting, ESG disclosure, and corporate governance literature by showing how non-financial disclosure can affect capital allocation efficiency and sustainable corporate decision-making.

## Further Information

This repository provides a project overview, methodology summary, selected empirical findings, and supporting documentation for academic portfolio purposes.

The full final year project report is not publicly uploaded because it was submitted as an academic assessment. Only selected project materials are included in this repository.

## License

This project is released under the MIT License. See LICENSE.md for more details.
