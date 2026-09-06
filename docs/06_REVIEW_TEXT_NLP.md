# Review Text Sentiment and NLP Intelligence

## 1. Methodology
Out of 100,000 reviews, 41,753 contain customer text comments (41.8%). A tokenization and frequency-ratio algorithm in Portuguese extracted terms that appear disproportionately in 1-2 star reviews relative to 4-5 star reviews.

\\text{Ratio}(w) = \\frac{\\text{Freq}_{\\text{low}}(w) / N_{\\text{low}}}{\\text{Freq}_{\\text{high}}(w) / N_{\\text{high}}}

---

## 2. Top Disproportionate Portuguese Keywords

| Portuguese Keyword | English Meaning | Bad Review Count | Ratio vs. Good Reviews | Root Cause Cluster |
| :--- | :--- | :--- | :--- | :--- |
| **decepcao / decepcionada** | disappointment | 842 | **127x** | Failed product / timing expectation |
| **descaso** | neglect / disregard | 412 | **119x** | Customer support responsiveness |
| **enganosa** | misleading / deceptive | 385 | **112x** | Inaccurate product description / photos |
| **falsificado** | counterfeit / fake | 192 | **57x** | Catalog vetting / counterfeit goods |
| **reembolso** | refund | 620 | **55x** | Return friction / delayed credit |
| **atrasada** | delayed / late | 1,480 | **45x** | Logistics delay |
| **estorno** | chargeback / refund | 315 | **40x** | Payment reversal dispute |
| **procon** | consumer protection agency | 185 | **27x** | Legal / regulatory complaint threats |

---

## 3. Qualitative Insights
1. **Catalog Integrity and Counterfeit Risk:** Mentions of alsificado (57x) and enganosa (112x) indicate customers encounter deceptive product descriptions and counterfeit items in electronics and audio. Olist needs automated catalog vetting.
2. **Escalation to Regulators:** Mentions of procon (27x) represent immediate regulatory and legal risk, as customers escalate unresolved shipping and refund delays to Brazil official consumer protection agency.
