# Executive Summary: Olist Marketplace Analysis
## Drivers of Customer Satisfaction on Brazil's Largest E-Commerce Integrator

**Event:** Data Analytics Hackathon - Gradient Learnings
**Team Name:** GenWin
**Team Leader:** Swati Dubey
**Team Member:** Nitanshu Tak
**Dataset:** Olist Brazilian E-Commerce Dataset (96,478 Delivered Orders, Sep 2016 - Oct 2018)

---

### Key Operational Metrics

| Metric | Measured Value | Practical Impact |
| :--- | :--- | :--- |
| **Delivered Orders Analyzed** | **96,478** | Order-level master table reconciled across 9 source tables |
| **Platform Mean Review** | **4.07 / 5.00** | Population baseline satisfaction |
| **Overall Late Rate** | **6.8%** | Orders arriving after estimated delivery date |
| **Review Score at 7+ Days Late** | **1.69 / 5.00** | Asymmetric threshold collapse in review ratings |
| **Multi-Seller Odds Ratio** | **6.47x** | Likelihood multiplier for 1-2 star reviews |
| **Repeat Customer Share** | **3.1% (5.7% Rev)** | Platform operates primarily as single-purchase acquisition |

---

### Core Structural Discoveries

#### 1. The Delivery Cliff Effect (Threshold Drop)
Customer satisfaction does not decline linearly with delivery time. Being early (1 to 14+ days ahead) yields minimal extra rating (4.17 to 4.30 average). However, crossing the promised estimated delivery date drops ratings immediately:
- **1 day late:** review drops from 4.28 to **2.70**.
- **7+ days late:** review collapses to **1.69**, with over 70% of customers leaving 1-star reviews.

#### 2. The Multi-Seller Coordination Deficit
Orders split across multiple sellers represent 1.3% of platform volume, but carry a **6.47x higher odds ratio** of receiving a 1- or 2-star rating.
- **Confound Isolation:** Even when restricting strictly to *on-time, small-basket orders (<= 3 items)*, multi-seller orders suffer a **46.0% bad review rate** versus **9.0%** for single-seller orders.
- The root cause is post-order coordination friction: fragmented tracking, split deliveries, and confusion rather than delivery transit speed.

#### 3. Seller-Customer Geographic Mismatch
- **59.7% of all sellers** are concentrated in Sao Paulo (SP), while SP represents only **42.0% of customer orders**.
- Cross-state shipments take twice as long (**14.7 days vs. 7.5 days**) and cost **75% more in freight** (R$ 26.96 vs. R$ 15.46).
- Northeast states suffer severe delay frequencies: Alagoas (**21%**), Maranhao (**18%**), Sergipe (**15%**), Ceara (**14%**), Piaui (**14%**).

#### 4. Payment Behavior is a Non-Driver (Validated Negative Result)
Multivariate logistic regression confirms that neither payment installment depth nor payment instrument type meaningfully drives review scores (OR = **1.02x**, p = 0.000). Debit card users reported the highest raw satisfaction (4.23 mean, 5.3% late rate). This negative finding allows Olist to avoid wasting engineering bandwidth on checkout payment overhauls.

---

### Strategic Action Matrix

| Priority Level | Strategic Initiative | Expected Business Impact |
| :--- | :--- | :--- |
| **Priority 1 (Urgent)** | Dynamic delivery estimate recalibration for cross-state orders and regional 3PL fulfillment hubs in Northeast (Recife/Salvador) | Eliminate the late-delivery cliff; reduce Northeast late rates from 18%+ to < 7% |
| **Priority 2 (Systemic)** | Unified tracking notifications and multi-package dashboard for split-seller orders | Reduce multi-seller bad-review rate from 46% to < 18% |
| **Priority 3 (Category)** | Packaging audits and heavy-carrier SLAs for Office Furniture and bulky categories | Lift Office Furniture ratings from 3.51 toward platform mean (4.07) |
| **Monitor Only** | Payment installment configurations and credit processing | Conserve software engineering bandwidth for logistics and tracking |
