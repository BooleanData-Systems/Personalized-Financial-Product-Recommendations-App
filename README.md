# Personalized Financial Product Recommendations

Leverage Apriori-based association rule mining to deliver personalized financial product recommendations based on customer demographics, risk profile, and current product holdings.

## What This App Does

The app uses pre-computed association rules to recommend financial products (credit cards, loans, insurance, investments, etc.) based on:

- **Age Group** — 18-24, 25-39, 40-54, 55+
- **Salary Band** — <50K, 50K-150K, 150K+
- **Risk Profile** — Low, Medium, High
- **Employment Status** — Salaried, Self-Employed, Business, Retired, Other
- **Current Product** — The customer's existing financial product

## How It Works

1. **Install the app** from the Marketplace listing.
2. **Open the app** — the Streamlit UI launches automatically.
3. **Set the customer profile** in the sidebar (age, salary, risk, employment, current product).
4. **View recommendations** — the app matches association rules to the profile and displays the top 5 recommended products ranked by confidence and support.

## Recommendation Logic

The app uses a 3-tier matching strategy:

1. **Exact segment match** — Rules matching all 4 demographic fields + current product
2. **Relaxed match** — Rules matching age group + salary band + current product
3. **Global fallback** — Universal rules based on current product only

## Data Included

This app ships with sample association rules and financial product data. No external data or table connections are required.

### PRODUCT_ASSOCIATIONS Table

| Column | Type | Description |
|---|---|---|
| `AGE_GROUP` | VARCHAR | Customer age segment or `GLOBAL` for fallback rules |
| `SALARY_BAND` | VARCHAR | Income segment or `GLOBAL` |
| `RISK_PROFILE` | VARCHAR | Risk tolerance or `GLOBAL` |
| `EMPLOYMENT_STATUS` | VARCHAR | Employment category or `GLOBAL` |
| `ANTECEDENT` | VARCHAR | Product(s) the customer currently holds |
| `CONSEQUENT` | VARCHAR | Recommended product(s) |
| `SUPPORT` | FLOAT | Rule support (0.0 to 1.0) |
| `CONFIDENCE` | FLOAT | Rule confidence (0.0 to 1.0) |
| `SCORE` | FLOAT | Combined score (support x confidence) |

### FIN_TABLE

| Column | Type | Description |
|---|---|---|
| `CURRENT_PRODUCT` | VARCHAR | Existing financial product |
| `RECOMMENDED_PRODUCT` | VARCHAR | Suggested next product |
| `CONVERSION_PROBABILITY` | FLOAT | Likelihood of conversion (0.0 to 1.0) |
| `OFFER_AVAILABLE` | VARCHAR | Whether an offer is currently available (`Yes` / `No`) |

## Available Products

Savings Account, Credit Card, Personal Loan, Home Loan, Mutual Fund, Insurance, Fixed Deposit, Pension Plan, Retirement Plan, Stocks, Portfolio Advisory, Wealth Management, Business Loan, Commercial Loan, Senior Savings Scheme.
