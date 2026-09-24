# Replication Data: The Diffusion of Digital Payments in India (2017-2026)

[![DOI](https://img.shields.io/badge/DOI-10.2139%2Fssrn.7478227-blue)](http://dx.doi.org/10.2139/ssrn.7478227)
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

This repository contains replication data for the work

> Gupta, Samarth, The Diffusion of Digital Payments in India: Empirical Evidence on UPI Adoption and Rail Substitution, 2017-2026 (September 17, 2026). Available at SSRN: [https://ssrn.com/abstract=7478227](https://ssrn.com/abstract=7478227) or [http://dx.doi.org/10.2139/ssrn.7478227](http://dx.doi.org/10.2139/ssrn.7478227).
---

## 1. Overview & Research Scope

This study analyzes United Payments Interface (UPI)'s adoption in India over an 111-month period (April 2017 – June 2026), focusing on:
1. UPI's Diffusion: From 7.20 million transactions (April 2017), UPI has grown to 22,716.07 million transactions (June 2026) and an average ticket size reduction
2. Substitution of Payment Rails: Cross-instrument comparison of Debit Cards, Credit Cards, CTS (Cheque Truncation System) and aggregated retail clearing
3. Network Effects: Onboarding dynamics at the extensive margin in the foundational-network-period (2017-2020)
---

## 2. Dataset Structure & Construction

The work analyzes two official statistics:
NPCI UPI Product Statistics (Monthly): Contains underlying diffusion statistics for UPI (monthly volumes, settlement values, and active banks), April 2017 to March 2020
RBI Table No. 45 (Payment System Indicators): Contains underlying statistic on cross instrument payments in Old Format (pre-November 2019) and New Format (November 2019 – June 2026)

### Primary panel
`data/processed/india_payment_rails_monthly_2017_2026.csv`: Contains harmonized monthly aggregates time series ($N=111$)
Primary window for estimation: November 2019 – June 2026 ($N=80$). A period chosen to avoid a structural break in Reporting methodology of the RBI in November 2019.
---

## 3. Key Empirical Findings

The volume multiple for UPI is 3,155x across the period (April 2017 – June 2026), while its ticket size has fallen by 59.6% (from ₹3,154 to ₹1,273). The hetergeneous displacement results are as follows (Nov 2019 – Jun 2026):
Debit Card Volume replaced: $-76.8\%$
CTS / Paper Clearing Volume replaced: $-50.8\%$
Credit Card Volume replaced: $+229.9\%$
Econometric estimates for the relationship between UPI and Debit Card show a negative association in a bivariate OLS ($\beta = -0.457$, HAC $p < 0.001$). This disappears when estimating a controlled specification (removing debit from retail payments), with the estimate turning positive ($\beta = +1.706$). This demonstrates that level regressions are capturing macroeconomic compositional shifts and not simple mechanical displacement.

## 4. Citation



If you use this dataset or findings in academic research or industry analysis, cite the paper as:



```bibtex

@article{gupta2026upi,

  title={The Diffusion of Digital Payments in India: Empirical Evidence on UPI Adoption and Rail Substitution, 2017--2026},

  author={Gupta, Samarth},

  journal={SSRN Electronic Journal},

  year={2026},

  month={September},

  doi={10.2139/ssrn.7478227},

  url={[http://dx.doi.org/10.2139/ssrn.7478227](http://dx.doi.org/10.2139/ssrn.7478227)}
