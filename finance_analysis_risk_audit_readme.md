# Finance Analysis & Portfolio Risk Dashboard

An enterprise-grade Power BI business intelligence and credit risk assessment project. This repository contains the analytics architecture, key operational findings, and a strategic remediation framework designed to de-risk an active **$253M lending book** across **3,134 borrowers**.

---

## 📌 Executive Summary

| Metric | Value | Description |
| :--- | :--- | :--- |
| **Total Loan Book** | **$253,000,000** | Cumulative principal capital extended |
| **Total Customer Count** | **3,134** | Active and historical borrower profiles |
| **Average Monthly Installment** | **$2.11K** | Mean debt service requirement per borrower |
| **Average Customer Income** | **$99.27K** | Mean annual earning capacity across borrowers |
| **Average Customer Age** | **44.00 Years** | Mid-career borrower demographic |
| **Capital in Distress** | **$154.16M (60.9%)** | Combined High-Risk ($127.97M) & Defaulted ($26.19M) exposure |

---

## 📊 Dashboard Architecture & Scope

The analytical solution is built across three dedicated reporting views:

```
Finance_Analysis_Dashboard/
│
├── 1. Customer Demographics
│   ├── Total Customers (3,134), Avg Age (44), Avg Income ($99.27K)
│   ├── Gender Distribution (Male 43.8%, Female 41.5%, Other 14.8%)
│   ├── Education Bifurcation (74%+ Higher Degree Attainment)
│   └── Credit Score Benchmarks by Demographics
│
├── 2. Loan Portfolio & Performance
│   ├── Book Exposure ($253M) & Repayment Burden ($2.11K/mo)
│   ├── Interest Rate Spread Gauge (3.01% Min – 15.00% Max)
│   ├── Product Diversification (Equal ~20% across 5 Loan Types)
│   └── Performance Status Breakdown (Active vs. Closed vs. Defaulted)
│
└── 3. Financial Risk Analysis
    ├── Capital Distress KPIs (519 Defaults / 2,547 High Risk)
    ├── Employment Risk Profiles (Full-Time, Self-Employed, Part-Time, Unemployed)
    ├── Credit Score Distribution vs. Customer Volume
    └── Income Tier Distress Matrix (High, Medium, Low Buckets)
```

---

## 🔍 Critical Problems Identified from Visuals

### 1. Severe High-Risk Capital Concentration ($127.97M Exposure)
* **Finding:** 2,547 out of 3,134 accounts (~81% of borrowers) represent $127.97M in high-risk exposure, while $26.19M across 519 accounts is already in complete default.
* **Root Cause:** Overly permissive underwriting algorithms approving applicants without adequate downside cash-flow stress testing.

### 2. High & Medium Income Earners Drive Majority Defaults ($20.15M+)
* **Finding:** The risk matrix indicates defaults are heavily concentrated in Medium ($1.00M+) and High income tiers ($1.01M+), rather than low-income accounts ($603K).
* **Root Cause:** Lending decisions were based on gross declared income rather than net disposable income and existing Debt-to-Income (DTI) obligations.

### 3. Subprime Credit Profile Skew
* **Finding:** The credit tier distribution shows that the largest borrower volume resides in the **"Poor"** credit tier, followed by **"Fair"**, with Prime categories representing the minority.
* **Root Cause:** High customer acquisition volumes driven by underwriting lower credit brackets without charging adequate risk-adjusted margins.

### 4. Rigid 20% Product Allocation (Excess Unsecured Exposure)
* **Finding:** Unsecured, high-loss lines (Personal and Small Business loans) hold an identical 20% share as collateralized, asset-backed lines (Mortgages and Auto loans).
* **Root Cause:** Absence of risk-weighted portfolio caps, exposing the institution to severe write-offs during borrower insolvency.

### 5. Equal Default Spread Across Employment Profiles
* **Finding:** Full-time salaried professionals account for ~27% of high-risk debt—matching or exceeding self-employed and unemployed categories.
* **Root Cause:** Absence of automated payroll deductions and salary sweeps, creating timing-related repayment defaults.

---

## 🛠️ Actionable Business Remediation Framework

| Identified Issue | Operational Root Cause | Actionable Strategic Solution |
| :--- | :--- | :--- |
| **$127.97M in High-Risk Exposure** | Unsecured lending to subprime applicants | **Mandatory Collateral & EWS:** Require a minimum 25% asset pledge/co-signer for scores below 620. Deploy an Early Warning System (EWS) reaching borrowers within 5 days of a missed due date. |
| **High Defaults in High Earners ($20.15M+)** | Gross income assessed without debt obligations | **Cap DTI at 40%:** Disallow approvals where monthly debt service exceeds 40% of net income. Implement tiered exposure limits on new high-earning accounts. |
| **Concentration in Subprime Tiers** | Flat interest pricing model | **Risk-Based Pricing (RBP):** Implement variable rates (14%–18%) for Poor/Fair tiers to fund a dedicated bad-debt loan-loss reserve (LLR). Use progressive step-up credit limits ($15K initial cap). |
| **40% Combined Unsecured Lending** | Fixed 20% quota across all products | **Portfolio Rebalancing:** Reallocate book mix toward asset-backed Mortgages and Auto loans (reducing Personal & Small Business exposure to < 20% combined). |
| **Salaried Delinquency (~27%)** | Manual repayment collection | **Automated Payroll Sweeps:** Integrate automatic ACH salary-day deductions and align due dates directly with verified corporate paydays. |
| **519 Stalled Defaults ($26.19M)** | Passive post-default recovery | **Restructuring & Settlement (OTS):** Extend tenors to reduce monthly installments by 30%–40% for 30–90 day delinquencies. Introduce targeted 70% lump-sum settlements and assign dedicated field agents for balances > $70K. |

---

## 📅 Phased Execution Roadmap

```
[Phase 1: 0 - 30 Days] ──► Immediate Capital Protection
                          ├── Enforce strict 40% DTI ceiling
                          ├── Freeze unsecured approvals for credit scores < 620
                          └── Launch automated 5-day Early Warning Desk

[Phase 2: 30 - 90 Days] ─► Portfolio De-Risking & Collections
                          ├── Deploy loan restructuring & tenor extensions
                          ├── Introduce mandatory ACH salary sweeps
                          └── Implement Risk-Based Pricing (RBP) tiers

[Phase 3: 90 - 180 Days] ─► Strategic Balance Sheet Optimization
                          ├── Rebalance portfolio toward secured asset lending
                          ├── Establish institutional Loan-Loss Reserves (LLR)
                          └── Institute automated quarterly stress-testing audits
```

---

## 💻 Tech Stack & Data Modeling

* **BI Platform:** Microsoft Power BI Desktop
* **Data Sources:** Core Banking OLTP (`Customer_Details`, `Loan_Details`, `Date`, `Analysis`)
* **Modeling Schema:** Star/Snowflake hybrid model with bidirectional dimension filtering
* **Key Analytical Calculations:**
  * Debt-to-Income (DTI) Ratios
  * Segmented Risk Buckets (Income & Credit Tier Dimensions)
  * Default Rate Exposure & Capital Loss Ratios