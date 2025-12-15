# ⚖️ Fairness-Optimized Credit Decisioning  
### Responsible AI for Financial Risk Modeling  
**By Danielle Bopda**

---

## 📘 Table of Contents
- [1. Executive Overview](#1-executive-overview)
- [2. Industry & Business Problem](#2-industry--business-problem)
- [3. Data Foundation & Financial Context](#3-data-foundation--financial-context)
- [4. Credit Modeling & Decision Framework](#4-credit-modeling--decision-framework)
- [5. Evaluation Metrics & Financial Meaning](#5-evaluation-metrics--financial-meaning)
  - [5.1 Quantitative Model Performance & Fairness Metrics](#51-quantitative-model-performance--fairness-metrics)
- [6. Visual Analysis: Business, Data & Financial Interpretation](#6-visual-analysis-business-data--financial-interpretation)
  - [6.1 Logistic Regression – Original Data](#61-logistic-regression--original-data)
  - [6.2 Logistic Regression – Fairness-Optimized Data](#62-logistic-regression--fairness-optimized-data)
  - [6.3 Multilayer Perceptron (MLP): Original vs Optimized](#63-multilayer-perceptron-mlp-original-vs-optimized)
  - [6.4 Random Forest: Original vs Optimized](#64-random-forest-original-vs-optimized)
  - [6.5 Bias Persistence Across Credit Data](#65-bias-persistence-across-credit-data)
- [7. Operational Impact Across Financial Stakeholders](#7-operational-impact-across-financial-stakeholders)
- [8. Strategic Insights & Deployable Solutions](#8-strategic-insights--deployable-solutions)
- [9. Assumptions, Constraints & Governance Requirements](#9-assumptions-constraints--governance-requirements)
- [10. Technologies Used](#10-technologies-used)
- [11. Final Note for Recruiters & Hiring Managers](#11-final-note-for-recruiters--hiring-managers)
- [12. Standards & Regulatory Alignment](#12-standards--regulatory-alignment)




---

## 1. Executive Overview

Credit decisioning systems directly shape a financial institution’s **profitability, regulatory exposure, customer inclusion, and long-term sustainability**. While machine learning models are often optimized for predictive accuracy, this project demonstrates a critical operational reality:

> **A model can be statistically accurate and financially harmful at the same time.**

This project evaluates how different credit models behave across approval thresholds, how bias manifests in approval decisions, and how fairness-aware preprocessing changes both **economic outcomes and regulatory risk**. The goal is not theoretical fairness, but **deployable, auditable, and economically rational decision systems**.

---

## 2. Industry & Business Problem

Financial institutions must continuously balance:
- Portfolio performance and default risk
- Fair lending compliance and regulatory scrutiny
- Customer trust and market expansion
- Explainability of automated decisions

Bias in credit models leads to:
- Systematic exclusion of creditworthy customers
- Reduced addressable market size
- Increased probability of regulatory penalties
- Expensive remediation after deployment

From a financial perspective, biased models are not just unethical—they are **economically inefficient** and **strategically fragile**.

---

## 3. Data Foundation & Financial Context

This analysis is based on the **German Credit Dataset**, a benchmark dataset widely used by banks, fintech firms, and regulators to study credit risk and discrimination.

### Financial relevance of the data:
- Features reflect borrower stability, liquidity, and repayment behavior
- Outcomes mirror approve/deny decisions used in lending pipelines
- Demographic attributes allow assessment of disparate impact

The structure mirrors **real underwriting data**, making insights directly applicable to operational credit systems.

---

## 4. Credit Modeling & Decision Framework

Three model families were evaluated to reflect real institutional choices:

- **Logistic Regression**  
  Favored in regulated environments due to interpretability, monotonicity, and auditability.

- **Multilayer Perceptron (MLP)**  
  Used when institutions attempt to capture nonlinear borrower behavior.

- **Random Forest**  
  Often proposed to maximize accuracy and short-term portfolio performance.

Each model was evaluated before and after fairness-aware preprocessing and across multiple thresholds, reflecting real **credit policy decisions**.

---

## 5. Evaluation Metrics & Financial Meaning

**Balanced Accuracy**  
Ensures that approval and rejection errors are treated symmetrically, which matters when denial errors represent **missed revenue opportunities**.

**Classification Threshold**  
Represents a **policy decision**, not a technical detail.  
Changing the threshold reallocates credit access and shifts risk across customer segments.

**Disparate Impact**  
Directly measures exposure to fair lending violations and regulatory enforcement.

Together, these metrics quantify the **tradeoff between profit, risk, and compliance**.

---

### 5.1 Quantitative Model Performance & Fairness Metrics

To support deployment-level evaluation, model performance and fairness were assessed using **quantified, regulator-relevant metrics** derived from threshold-level analysis.

**Balanced Accuracy**  
Across all evaluated models, balanced accuracy ranged approximately between **0.66 and 0.74**.  
Following fairness-aware preprocessing, balanced accuracy declined by approximately **3–6 percentage points**, depending on model complexity.  
This reflects an acceptable performance trade-off in regulated credit environments where compliance and stability are prioritized over marginal accuracy gains.

**Disparate Impact**  
Prior to bias mitigation, disparate impact deviated materially from parity, with deviations of approximately **15–30%** observed at performance-optimal thresholds.  
After optimized preprocessing, deviations were reduced to approximately **5–10%**, substantially lowering fair lending and regulatory risk.

**Threshold Sensitivity**  
Fairness outcomes were highly sensitive to classification thresholds.  
For more complex models, small threshold adjustments (±0.05) produced **10–20% swings in disparate impact**, demonstrating that threshold selection must be treated as a governed business decision rather than a default technical parameter.

**Model Stability**  
Interpretable models exhibited significantly more stable fairness behavior across thresholds.  
Ensemble models showed approximately **2–3× higher fairness volatility**, increasing monitoring, audit, and remediation costs over time.

**Accuracy–Fairness Trade-off**  
The analysis demonstrates that a modest reduction in predictive performance (**~3–6%**) yielded a disproportionate improvement in fairness outcomes (**~50–70% reduction in deviation from parity**), representing a **positive risk-adjusted outcome** for financial institutions.

---

## 6. Visual Analysis: Business, Data & Financial Interpretation

This section mirrors how analytics, risk, compliance, and executive teams jointly review models.

---

### 6.1 Logistic Regression – Original Data

![Logistic Regression Original](assets/Logistic%20Regression%20(original%20notebook).1.png)
![Logistic Regression Original](assets/Logistic%20Regression%20(original%20notebook).2.png)
![Logistic Regression Original](assets/Logistic%20Regression%20(original%20notebook).3.png)

#### Data & Econometric Interpretation
The model displays stable balanced accuracy across thresholds, indicating statistical robustness. However, disparate impact increases significantly near economically optimal thresholds.

This indicates that the model’s coefficients, while interpretable, encode **structural correlations** that disadvantage protected groups.

#### Financial Meaning
At thresholds where profitability is maximized, the institution simultaneously:
- Rejects a higher proportion of certain demographic groups
- Shrinks its future customer base
- Increases regulatory exposure

This is a classic **hidden cost** scenario: profit appears strong, but long-term risk accumulates.

---

### 6.2 Logistic Regression – Fairness-Optimized Data

![Debiased Logistic Regression](assets/Debiased-Data%201.png)
![Debiased Logistic Regression](assets/Debiased-Data%202.png)

#### Data & Econometric Interpretation
Fairness-aware preprocessing reshapes feature distributions to reduce correlation with protected attributes. The result is smoother, more stable disparate impact across thresholds.

Balanced accuracy declines slightly but remains statistically acceptable.

#### Financial Meaning
This represents a **risk-adjusted optimization**:
- Slightly lower short-term accuracy
- Substantially lower compliance and litigation risk
- More stable approval policies over time

For most institutions, this is a **positive net-value tradeoff**.

---

### 6.3 Multilayer Perceptron (MLP): Original vs Optimized

![MLP Original](assets/MLP%201.png)
![MLP Optimized](assets/MLP%202.png)

#### Data & Econometric Interpretation
The MLP captures nonlinear effects but shows high sensitivity to threshold changes. Bias fluctuates unpredictably, especially in the original configuration.

Debiasing improves parity but does not eliminate instability.

#### Financial Meaning
From an operational standpoint:
- Nonlinear models increase monitoring costs
- Explainability challenges complicate audits
- Governance overhead rises significantly

Without strong controls, such models may **increase total cost of ownership**, even if accuracy improves.

---

### 6.4 Random Forest: Original vs Optimized

![Random Forest Original](assets/Random%20Forest%201.png)
![Random Forest Optimized](assets/Random%20Forest%202.png)

#### Data & Econometric Interpretation
Random Forest delivers the highest accuracy but exhibits the most volatile disparate impact across thresholds. Even after preprocessing, fairness remains unstable.

This reflects how ensemble models amplify subtle correlations across many trees.

#### Financial Meaning
This is a **classic executive dilemma**:
- High accuracy improves short-term portfolio metrics
- Volatile fairness increases regulatory and reputational risk
- Explainability limitations hinder defensibility

In many regulated environments, this model would **fail governance review**, despite its performance.

---

### 6.5 Bias Persistence Across Credit Data

![Original Credit Bias](assets/Original-Data%201.png)
![Original Credit Bias](assets/Original-Data%202.png)

#### Interpretation
Bias patterns recur across datasets and model types, demonstrating that fairness issues are **systemic** rather than accidental.

#### Strategic Meaning
This confirms that fairness must be addressed at the **process level**, not model-by-model. Governance frameworks are essential.

---

## 7. Operational Impact Across Financial Stakeholders

- **Risk Teams**  
  Gain early visibility into approval inequities.

- **Compliance Teams**  
  Obtain measurable, documented mitigation strategies.

- **Product Teams**  
  Understand how approval policies affect inclusion and growth.

- **Executives**  
  Reduce regulatory exposure while maintaining sustainable profitability.

---

## 8. Strategic Insights & Deployable Solutions

- Optimize models for **risk-adjusted performance**, not raw accuracy
- Treat thresholds as policy levers, not technical defaults
- Favor interpretable models in high-stakes decisions
- Integrate fairness checks into standard validation workflows
- Monitor fairness continuously post-deployment

These practices directly support **profitable, compliant AI adoption**.

---

## 9. Assumptions, Constraints & Governance Requirements

- Public benchmark data used for methodology demonstration
- Static snapshot; production systems require ongoing monitoring
- Preprocessing mitigates bias but does not eliminate all inequities
- Strong governance and audit controls are mandatory in deployment

---

## 10. Technologies Used

- Python  
- scikit-learn  
- AI Fairness 360 (AIF360)  
- Pandas, NumPy  
- Matplotlib  

---

## 11. Final Note for Recruiters & Hiring Managers

This project demonstrates how credit models must be evaluated **as economic systems**, not just statistical artifacts. It shows the judgment required to balance profit, risk, compliance, and customer impact in real financial environments.

The emphasis is not on maximizing accuracy—but on maximizing **long-term, defensible business value**.

---

## 12. Standards & Regulatory Alignment

This project aligns with established regulatory, industry, and Responsible AI standards used in financial institutions and fintech environments.

| Area | Standard / Authority | How This Project Aligns |
|---|---|---|
| Fair Lending | CFPB Fair Lending Examination Procedures | Explicit measurement of disparate impact and approval-rate parity |
| Model Risk Management | Federal Reserve SR 11-7 | Documented model behavior, limitations, and tradeoffs |
| Responsible AI | NIST AI Risk Management Framework | Evaluation of fairness, explainability, and governance risk |
| Bias Mitigation | IBM AI Fairness 360 (AIF360) | Application of optimized preprocessing to reduce discrimination |
| Automated Decision Rights | GDPR Article 22 | Emphasis on explainable, defensible credit decisions |
| Credit Modeling Practice | German Credit Dataset (UCI) | Industry-standard benchmark for credit risk and bias analysis |
| Business Thresholding | Data Science for Business (Provost & Fawcett) | Thresholds treated as business policy decisions |

This alignment demonstrates how fairness-aware modeling can be integrated into real-world credit decision pipelines while meeting regulatory and governance expectations.
