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

### Interactive Explorer (Tab 1)

1. **Install the app** from the Marketplace listing.
2. **Open the app** — the Streamlit UI launches automatically.
3. **Set the customer profile** in the sidebar (age, salary, risk, employment, current product).
4. **View recommendations** — the app matches association rules to the profile and displays the top 5 recommended products ranked by confidence and support.

### Batch Recommendations with Your Own Data (Tab 2)

The app supports **consumer-provided customer data**. You can connect your own customers table and generate personalized recommendations for every customer in bulk.

#### Required Table Schema

Your customers table must have the following columns:

| Column | Type | Description |
|---|---|---|
| `CUSTOMER_ID` | VARCHAR | Unique customer identifier |
| `AGE` | NUMBER | Customer age (e.g. 35) |
| `SALARY` | NUMBER | Annual salary (e.g. 75000) |
| `RISK_PROFILE` | VARCHAR | `Low`, `Medium`, or `High` |
| `EMPLOYMENT_STATUS` | VARCHAR | `Salaried`, `Self-Employed`, `Business`, `Retired`, or `Other` |
| `CURRENT_PRODUCT` | VARCHAR | Current financial product (e.g. `SAVINGS ACCOUNT`, `CREDIT CARD`) |

#### How to Connect Your Table

**Option A — Via Snowsight UI:**
1. Navigate to the installed app in **Catalog > Apps**
2. Click the **Settings** icon > **Privileges** tab
3. Under **Object access privileges**, click **Add** next to "Customer table"
4. Select the table containing your customer data
5. Click **Save**
6. Open the app and go to the **Batch Recommendations** tab
7. Click **Generate Recommendations**

**Option B — Via SQL:**
```sql
CALL <app_name>.config.register_single_reference(
  'consumer_customers',
  'ADD',
  SYSTEM$REFERENCE('TABLE', '<your_db>.<your_schema>.<your_table>', 'PERSISTENT', 'SELECT')
);
