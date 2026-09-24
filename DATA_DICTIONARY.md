### 2. `DATA_DICTIONARY.md`

```markdown
# Data Dictionary: Indian Payment-Rail Diffusion Panel (2017–2026)

This document defines the schema, operational definitions, mathematical transformations, and regulatory provenance for all variables in the harmonized monthly panel: `india_payment_rails_monthly_2017_2026.csv`.

---

## 1. Temporal & Network Identifiers

| Variable | Type | Unit | Description | Regulatory Provenance |
| :--- | :--- | :--- | :--- | :--- |
| `Month_Year` | String | YYYY-MM | Observation month and calendar year (2017-04 to 2026-06). | Common Index |
| `Time_Index` | Integer | Count | Sequential discrete time step ($t = 1, 2, \dots, 111$). | Author Calculation |
| `Banks_Live` | Integer | Count | Cumulative number of commercial/payment banks live on UPI network. Available for foundational phase (2017-04 to 2020-03). | NPCI Product Statistics |

---

## 2. UPI Diffusion Series

| Variable | Type | Unit | Formula / Definition | Regulatory Provenance |
| :--- | :--- | :--- | :--- | :--- |
| `UPI_Vol` | Float | Millions | Total successful UPI transactions completed during the calendar month. Lakh values divided by 10. | NPCI (2017–2020); RBI Table 45 (2020–2026) |
| `UPI_Value` | Float | INR Crores | Total gross clearing value settled via UPI rail during the month. | NPCI (2017–2020); RBI Table 45 (2020–2026) |
| `AvgTicket` | Float | INR / Trans. | Average transaction value (ticket size): `(UPI_Value * 10) / UPI_Vol`. (₹1 Crore per 1 Million transactions = ₹10/trans). | Author Calculation |

---

## 3. Cross-Instrument Payment Rails

| Variable | Type | Unit | Operational Scope | Regulatory Provenance |
| :--- | :--- | :--- | :--- | :--- |
| `DC_Vol` | Float | Millions | Total Point-of-Sale (POS) and E-Commerce debit card transaction volume. | RBI Table No. 45 (Payment System Indicators) |
| `DC_Value` | Float | INR Crores | Total monetary throughput cleared on debit cards. | RBI Table No. 45 |
| `CC_Vol` | Float | Millions | Total Point-of-Sale (POS) and E-Commerce credit card transaction volume. | RBI Table No. 45 |
| `CC_Value` | Float | INR Crores | Total monetary throughput cleared on credit cards. | RBI Table No. 45 |
| `CTS_Vol` | Float | Millions | Cheque Truncation System (CTS) paper clearing volume. | RBI Table No. 45 |
| `CTS_Value` | Float | INR Crores | Total value cleared through CTS paper clearing mechanisms. | RBI Table No. 45 |

---

## 4. Macro & Econometric Controls

| Variable | Type | Unit | Formula / Definition | Econometric Role |
| :--- | :--- | :--- | :--- | :--- |
| `Retail_Vol` | Float | Millions | Aggregate retail payment transaction volume as reported under RBI New Format. | Macroeconomic control |
| `RetailExDebit` | Float | Millions | Total retail volume net of debit card volume: `Retail_Vol - DC_Vol`. | Eliminates mechanical endogeneity in Model 2 |
| `ln_UPI_Vol` | Float | Log Scale | $\ln(\text{UPI\_Vol})$. | Primary regressor |
| `ln_DC_Vol` | Float | Log Scale | $\ln(\text{DC\_Vol})$. | Dependent variable (Models 1 & 2) |
| `ln_CC_Vol` | Float | Log Scale | $\ln(\text{CC\_Vol})$. | Dependent variable (Model 3) |
| `ln_RetailExDebit` | Float | Log Scale | $\ln(\text{RetailExDebit})$. | Control regressor (Model 2) |
| `ln_Banks_Live` | Float | Log Scale | $\ln(\text{Banks\_Live})$. | Network proxy (Model 4) |

---

## 5. Measurement Notes & Break Cautions

1. **November 2019 Format Revision:** In November 2019, the RBI implemented a revised reporting framework (Table No. 45 New Format) with more granular categorization for card and prepaid payment instruments (PPI). To preserve statistical validity, regression models (1–3) are estimated strictly on the post-break window ($N=80$, November 2019 – June 2026).
2. **Denomination Conversions:** Official RBI publications report volume in **Lakhs** ($10^5$) and value in **Crores** ($10^7$). For econometric consistency, all volumes are converted to **Millions** ($10^6$) by dividing by $10$.
