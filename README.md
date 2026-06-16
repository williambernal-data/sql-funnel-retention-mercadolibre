# sql-funnel-retention-mercadolibre
SQL funnel analysis and cohort retention (D7/D14/D21/D28) for MercadoLibre using CTEs and LEFT JOINs. Identifies conversion drop-offs and retention patterns across 10 Latin American countries.
# Funnel & Retention Analysis — MercadoLibre
**Tool:** SQL (PostgreSQL) | **Period:** 2025-01-01 → 2025-08-31 

---

## Context

As a product analyst at MercadoLibre's Growth & Retention team, the objective was to map the full conversion funnel, identify the main drop-off points, and evaluate user retention by cohort — to propose actionable improvements backed by data.

**Business questions:**
1. At which funnel stage do we lose the most users?
2. How does this loss vary by country?
3. How well do we retain users over time (D7 / D14 / D21 / D28)?
---

## Key Insights

- Overall funnel conversion from first visit to purchase was only 1.25%.
- The largest conversion loss occurred between Product Selection and Add to Cart (-65.89 percentage points).
- Uruguay achieved the highest purchase conversion rate (4.55%), outperforming all other markets.
- Paraguay recorded 0% purchase conversion, suggesting a potential operational or checkout issue.
- User retention dropped from approximately 85.5% at D7 to only 2.4% at D28.
- Mexico and Peru showed the strongest long-term retention, indicating higher user engagement and loyalty.
---

## Part 1 — Conversion Funnel

### Overall Funnel Conversion Rates

| Stage | Conversion Rate |
|---|---|
| Select Item | 76.90% |
| Add to Cart | 11.01% |
| Begin Checkout | 4.00% |
| Add Shipping Info | 2.42% |
| Add Payment Info | 2.09% |
| Purchase | 1.25% |

> **Key finding:** The biggest drop-off occurs between Select Item and Add to Cart (**-65.89 percentage points**) — the single highest-leverage point for product and UX improvements.

---

### Funnel Conversion by Country

| Country | Select Item | Add to Cart | Begin Checkout | Add Shipping | Add Payment | Purchase |
|---|---|---|---|---|---|---|
| Uruguay | 81.82% | 22.73% | 4.55% | 4.55% | 4.55% | 4.55% |
| Bolivia | 80.65% | 9.68% | 3.23% | 3.23% | 3.23% | 3.23% |
| Mexico | 79.75% | 13.22% | 4.13% | 3.31% | 2.89% | 2.48% |
| Peru | 84.55% | 10.00% | 2.73% | 2.73% | 1.82% | 1.82% |
| Argentina | 75.00% | 8.75% | 4.38% | 1.88% | 1.88% | 1.25% |
| Chile | 78.35% | 17.53% | 8.25% | 3.09% | 2.06% | 1.03% |
| Brazil | 72.60% | 8.90% | 2.40% | 1.37% | 1.37% | 0.68% |
| Ecuador | 74.58% | 10.17% | 5.08% | 1.69% | 1.69% | 0.00% |
| Colombia | 76.36% | 9.70% | 4.85% | 3.03% | 2.42% | 0.00% |
| Paraguay | 71.43% | 9.52% | 0.00% | 0.00% | 0.00% | 0.00% |

---

## Part 2 — User Retention

### Retention Rate by Country (D7 / D14 / D21 / D28)

| Country | D7 | D14 | D21 | D28 |
|---|---|---|---|---|
| Argentina | 85.1% | 52.3% | 22.5% | 1.8% |
| Bolivia | 80.8% | 46.8% | 19.2% | 2.5% |
| Brazil | 87.2% | 54.4% | 24.4% | 2.5% |
| Chile | 83.7% | 51.8% | 22.1% | 1.7% |
| Colombia | 84.5% | 52.0% | 21.8% | 1.6% |
| Ecuador | 79.1% | 50.0% | 20.6% | 2.5% |
| Mexico | 86.1% | 55.8% | 25.5% | 3.1% |
| Paraguay | 80.9% | 49.1% | 22.1% | 2.1% |
| Peru | 84.3% | 51.1% | 22.9% | 3.2% |
| Uruguay | 86.1% | 48.8% | 23.0% | 2.5% |

---

### Retention Rate by Monthly Cohort

| Cohort | D7 | D14 | D21 | D28 |
|---|---|---|---|---|
| 2025-01 | 86.2% | 56.2% | 24.1% | 3.0% |
| 2025-02 | 86.8% | 56.0% | 24.6% | 2.7% |
| 2025-03 | 87.7% | 56.8% | 26.6% | 3.0% |
| 2025-04 | 87.2% | 53.9% | 23.0% | 2.0% |
| 2025-05 | 86.0% | 54.5% | 26.2% | 3.0% |
| 2025-06 | 85.9% | 55.1% | 25.2% | 2.1% |
| 2025-07 | 86.4% | 56.4% | 25.9% | 2.7% |
| 2025-08 | 70.8% | 29.7% | 7.5% | 0.2% |

> **Note:** The 2025-08 cohort shows lower retention because users registered in August had fewer days to reach D14/D21/D28 within the analysis window.

---

## Executive Summary (C → F → I)

### Question 1: Where do we lose the most users?

**Context:** We analyzed the full conversion funnel from first visit to purchase for the period Jan–Aug 2025.

**Finding:** Conversion rates by stage: Select Item 76.90% → Add to Cart 11.01% → Begin Checkout 4.00% → Add Shipping 2.42% → Add Payment 2.09% → Purchase 1.25%. The steepest drop occurs between Select Item and Add to Cart (-65.89 pp). Uruguay leads in purchase conversion (4.55% add to cart: 22.73%) while Paraguay shows 0% completed purchases.

**Implication:**
1. The -65.89% drop between Select Item and Add to Cart is the largest funnel leak and the highest-ROI optimization opportunity. Before investing more in user acquisition, the priority should be reviewing the product experience at that stage: pricing competitiveness, image quality, descriptions, and page load times.
2. A/B testing on the Add to Cart flow should be implemented to identify the specific friction point stopping users.
3. Paraguay requires urgent investigation — 0% completed purchases signals an operational or coverage issue. Marketing investment in Paraguay should be paused until the root cause is resolved.

---

### Question 2: How well do we retain users over time?

**Context:** We analyzed user retention by cohort (D7/D14/D21/D28) for users registered Jan–Aug 2025, segmented by country.

**Finding:** Strong initial D7 retention (~85.5% average) collapses to ~2.4% by D28. Countries with strongest D7 retention: Brazil (87.2%), Mexico (86.1%), Uruguay (86.1%). Countries with strongest D28 retention: Peru (3.2%), Mexico (3.1%).

**Implication:**
1. Brazil, Mexico, and Uruguay show the strongest D7 retention — reactivation campaigns targeting the D7→D14 window in these countries have the highest potential to recover users before permanent churn.
2. Peru and Mexico are the only markets with meaningful D28 retention. Investigating what differentiates these users (segment, product category, acquisition channel) could reveal the ideal customer profile that actually returns.
3. The D7→D14 window is where most users are lost. Push notifications, loyalty incentives, or personalized re-engagement emails in that window could meaningfully shift the retention curve.

---

## SQL Structure

| Section | Description |
|---|---|
| Part 1 — Schema exploration | `LIMIT 5` on both tables + distinct events |
| Part 2 — Overall funnel | 7 CTEs + LEFT JOINs anchored on first_visit |
| Part 2 — Funnel by country | Same logic + country as JOIN key + GROUP BY |
| Part 3 — Retention counts | `COUNT DISTINCT CASE WHEN` per D7/D14/D21/D28 |
| Part 3 — Retention % by country | Same + division by total unique users |
| Part 4 — Cohort definition | `DATE_TRUNC` + `TO_CHAR` for YYYY-MM format |
| Part 4 — Retention by cohort | CTE chain: cohort → activity → final SELECT |
