# ⚖️ Fairness-Optimized Credit Decisioning  
### *Responsible AI for Financial Risk Modeling*  
**By Danielle Bopda**

---

## 📘 Table of Contents
- [1. Project Overview](#1-project-overview)
- [2. Business Context](#2-business-context)
- [3. Data & Fairness Diagnostics](#3-data--fairness-diagnostics)
- [4. Executive Summary](#4-executive-summary)
  - [4.1 Key Findings](#41-key-findings)
  - [4.2 Accuracy–Fairness Tradeoff](#42-accuracyfairness-tradeoff)
- [5. Deep-Dive Analysis (Visuals + Interpretation + Business Value)](#5-deep-dive-analysis-visuals--interpretation--business-value)
  - [5.1 Logistic Regression – Original Data](#51-logistic-regression--original-data)
  - [5.2 Logistic Regression – Fairness-Optimized Data](#52-logistic-regression--fairness-optimized-data)
  - [5.3 Threshold Sensitivity & Bias Escalation](#53-threshold-sensitivity--bias-escalation)
- [6. Key Performance Indicators (KPIs)](#6-key-performance-indicators-kpis)
- [7. Recommendations](#7-recommendations)
- [8. Real-World Impact & Industry Relevance](#8-real-world-impact--industry-relevance)
- [9. Assumptions & Limitations](#9-assumptions--limitations)
- [10. Technologies Used](#10-technologies-used)

---

# 1. **Project Overview**

This project examines a critical issue in financial machine learning:

> **A credit model can be accurate and still be unfair.**

I built and evaluated a **fairness-aware credit decisioning pipeline** that explicitly measures and mitigates demographic bias while maintaining usable predictive performance.

Rather than optimizing for accuracy alone, this work focuses on:

- **Balanced Accuracy** for imbalanced financial data  
- **Disparate Impact** as a fairness metric  
- **Classification threshold behavior**, where real-world bias often emerges  

This project mirrors **real production tradeoffs** faced by banks, fintech lenders, and regulated financial institutions.

---

# 2. **Business Context**

Credit decision systems directly affect:

- Loan approvals and denials  
- Financial inclusion and exclusion  
- Regulatory compliance (Fair Lending, ECOA, GDPR)  
- Legal and reputational risk  

In many organizations, models are optimized for headline accuracy metrics while **bias remains invisible**.

This creates risk in the form of:

- Discriminatory approval patterns  
- Regulatory penalties  
- Model audit failures  
- Long-term trust erosion  

Responsible AI in finance is **not theoretical** — it is operational risk management.

---

# 3. **Data & Fairness Diagnostics**

This project uses structured credit datasets containing:

- Financial attributes (income, employment, credit history)  
- Demographic attributes (protected classes)  
- Binary outcomes (approve / deny)  

Before mitigation, I evaluated:

- Balanced Accuracy across classification thresholds  
- Disparate Impact across thresholds  
- Sensitivity of fairness to decision policy  

I then applied **Optimized Preprocessing** to debias the data before model training.

This reflects **pre-deployment diagnostics** expected in regulated financial environments.

---

# 4. **Executive Summary**

## 4.1 **Key Findings**

- Logistic Regression on original data achieves strong accuracy but exhibits **clear demographic bias**.
- Fairness degradation intensifies near performance-optimal thresholds.
- Optimized Preprocessing substantially reduces bias with a **moderate accuracy tradeoff**.
- Threshold selection has **as much impact on fairness as model choice**.

These findings align with real-world Responsible AI audits.

---

## 4.2 **Accuracy–Fairness Tradeoff**

There is no free optimization.

- Maximum accuracy often coincides with **maximum bias**.
- Bias mitigation slightly reduces accuracy but **dramatically improves equity**.
- The correct solution is **controlled, transparent tradeoff**, not blind optimization.

This project quantifies that tradeoff explicitly.

---

# 5. **Deep-Dive Analysis (Visuals + Interpretation + Business Value)**

---

## 5.1 **Logistic Regression – Original Data**

![Balanced Accuracy vs Disparate Impact (Original)](ac89bded-8747-4fbb-a811-13a8e3f78a92.png)

### Interpretation

- Balanced Accuracy peaks near a mid-range classification threshold.
- Disparate Impact increases sharply at the same operating point.
- The dashed vertical line marks the threshold that maximizes accuracy but **not fairness**.

### Business Value

- A model can pass accuracy benchmarks while failing fairness audits.
- Deploying this configuration would expose institutions to **regulatory and legal risk**.
- This visualization makes hidden bias **visible and measurable**.

---

## 5.2 **Logistic Regression – Fairness-Optimized Data**

![Balanced Accuracy vs Disparate Impact (Debiased)](1f0e8bd5-3798-407f-a04a-8c286b34e890.png)

### Interpretation

- Balanced Accuracy decreases slightly compared to the original model.
- Disparate Impact remains near **1.0** across most thresholds.
- Bias no longer spikes at performance-optimal thresholds.

### Business Value

- Optimized Preprocessing successfully **decouples performance from discrimination**.
- This configuration is **deployable in regulated environments**.
- The accuracy loss is a **known and acceptable governance tradeoff**.

---

## 5.3 **Threshold Sensitivity & Bias Escalation**

![Threshold Sensitivity Plot](e6005155-8979-4281-a481-a4be356f50d6.png)

![Threshold Sensitivity Plot](31686310-a38b-47f0-94eb-a7b83252cd64.png)

![Threshold Sensitivity Plot](ad1311e5-189b-4355-a785-123d84b859b9.png)

### Interpretation

- Fairness metrics are **highly sensitive to threshold changes**.
- Small policy shifts can cause **large demographic disparities**.
- Bias escalation often occurs silently unless explicitly monitored.

### Business Value

- Threshold tuning is a **governance decision**, not just a technical one.
- Institutions must document and justify operating points.
- This analysis supports **audit readiness and defensible decision-making**.

---

# 6. **Key Performance Indicators (KPIs)**

| KPI | Result | Business Meaning |
|----|-------|----------------|
| Balanced Accuracy | ~0.70–0.75 | Strong predictive power under imbalance |
| Disparate Impact (Original) | High deviation | Unacceptable bias risk |
| Disparate Impact (Mitigated) | ≈ 1.0 | Fair treatment across groups |
| Accuracy Tradeoff | ~5–10% | Acceptable regulatory cost |
| Threshold Stability | High (post-mitigation) | Safer deployment |

---

# 7. **Recommendations**

### For Financial Institutions
- Do not deploy credit models without **fairness diagnostics**.
- Treat thresholds as **policy controls**, not defaults.
- Favor interpretable, auditable models when risk exposure is high.

### For Data & ML Teams
- Evaluate fairness across **entire threshold ranges**.
- Integrate bias metrics into CI/CD pipelines.
- Monitor fairness drift post-deployment.

### For Executives & Risk Leaders
- Responsible AI reduces **long-term legal and reputational risk**.
- Fairness-aware systems increase institutional resilience.
- Bias mitigation is **risk management**, not model degradation.

---

# 8. **Real-World Impact & Industry Relevance**

This work directly applies to:

- Retail and commercial banking  
- Fintech lending platforms  
- Credit scoring vendors  
- Model risk management teams  
- Regulatory audits  

A system like this can:

- Prevent discriminatory lending outcomes  
- Reduce compliance exposure  
- Improve trust and transparency  
- Support defensible credit decisions  

---

# 9. **Assumptions & Limitations**

- Datasets are static; real systems require continuous monitoring.
- Fairness metrics reflect observed data, not societal causality.
- Preprocessing reduces bias but does not eliminate all inequities.
- Production deployment requires governance and audit controls.

These constraints reflect **real financial AI systems**, not academic idealizations.

---

# 10. **Technologies Used**

- Python  
- Scikit-learn  
- IBM AIF360  
- NumPy, Pandas  
- Matplotlib  
- Jupyter Notebook  

---

# 📌 Final Note

This project is intentionally practical.

It demonstrates:
- Technical rigor  
- Fairness literacy  
- Regulatory awareness  
- Business judgment  

It is designed for **real financial decision systems**, not leaderboard optimization.
