# Exploratory Data Analysis and Empirical Patterns

## 1. Order Volume vs Review Scores Over Time
From early 2017 to mid-2018, Olist experienced a ~5x increase in monthly order volume, expanding from ~1,330 orders per month to over 6,600 orders per month. Revenue tracked order volume closely.

Review scores tell a more nuanced story:
- Maintained 4.05 to 4.25 throughout most of 2017.
- **Dipped to 3.90 in November 2017:** Correlated directly with **Black Friday (November 24, 2017)** where carrier and warehouse operational volume surged.
- Dipped to 3.81 / 3.74 in February-March 2018 before rebounding to platform-record highs of **4.25+** by mid-2018.

---

## 2. Product Category Disparities and Confidence Testing
Across 54 categories with >= 80 orders, 95% confidence intervals were computed against the platform mean (4.07):

\\text{CI}_{95\\%} = \\bar{x} \\pm 1.96 \\cdot \\frac{s}{\\sqrt{n}}

### Statistically Underperforming Categories (p < 0.05)
- **Office Furniture:** 3.51 mean (n=1,254, CI: [3.42, 3.59]) - Bulky, freight damage
- **Fashion Male Clothing:** 3.73 mean (n=106, CI: [3.42, 4.05]) - Sizing mismatches
- **Fixed Telephony:** 3.75 mean (n=212, CI: [3.54, 3.95]) - Defective hardware
- **Audio:** 3.82 mean (n=348, CI: [3.66, 3.98]) - High expectations / complaints
- **Home Comfort:** 3.86 mean (n=392, CI: [3.72, 4.01]) - Bulky shipping cost
- **Bed, Bath and Table:** 3.91 mean (n=9,272, CI: [3.88, 3.93]) - Seller quality variance
- **Furniture Living Room:** 3.91 mean (n=414, CI: [3.77, 4.05]) - Handling delays
- **Furniture Decor:** 3.94 mean (n=6,307, CI: [3.91, 3.98]) - Fragile transit breakage

### Top Categories
- **Books (Technical and General):** 4.37 - 4.45 (rigid packaging, low damage risk)
- **Food and Drink:** 4.32 (rapid consumable dispatch)
- **Luggage and Accessories:** 4.31 (durable construction)
