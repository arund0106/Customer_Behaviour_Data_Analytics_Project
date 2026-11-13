# 🛍️ Customer Shopping Behavior Analysis

An end-to-end data analytics project that cleans a retail customer dataset with **Python**, answers 10 business questions with **SQL**, and presents the findings in an interactive **Power BI** dashboard.

---

## 📌 Overview

Retail businesses need to know *who* their customers are, *what* they buy, and *what drives* their spending. This project analyzes 3,900 customer transactions to uncover patterns in:

- Revenue by gender, age group, and product category
- Impact of subscriptions, discounts, and shipping type on spending
- Customer loyalty segments and repeat-buyer behavior
- Top products and top-performing states

**Workflow:** Raw CSV → Python (cleaning & feature engineering) → SQL (business analysis) → Power BI (dashboard)

---

## 📂 Dataset

| Item | Details |
|---|---|
| Records | 3,900 customer purchases |
| Raw columns | 18 |
| Cleaned columns | 19 (after feature engineering) |
| Unique customers | 3,900 (one row per Customer ID) |

**Key columns:** `customer_id`, `age`, `gender`, `item_purchased`, `category`, `purchase_amount`, `location`, `season`, `review_rating`, `subscription_status`, `shipping_type`, `discount_applied`, `previous_purchases`, `payment_method`, `frequency_of_purchases`

**Engineered columns:**
- `age_group` – customers split into 4 equal groups (Young-Adult, Adult, Mid-Aged, Senior) using quartiles
- `purchase_frequency_days` – purchase frequency converted to a number of days (e.g., Weekly = 7, Monthly = 30)

---

## 🛠️ Tools

| Tool | Purpose |
|---|---|
| **Python (Pandas)** in Jupyter Notebook | Data cleaning and feature engineering |
| **SQL** | Business analysis and insights |
| **Power BI** | Interactive dashboard |
| **GitHub** | Version control and project sharing |

---

## 🔄 Steps

### 1. Data Cleaning & Preparation (Python)
- Loaded the dataset and checked structure, data types, and summary statistics
- Confirmed `Customer ID` is unique
- Filled missing **Review Rating** values with the **median rating of each product category**
- Standardized column names (lowercase, underscores, removed `(USD)`)
- Created `age_group` using quartile binning
- Created `purchase_frequency_days` from the purchase frequency text
- Dropped `promo_code_used` because it was identical to `discount_applied`
- Exported the result as `customer_shopping_behavior_clean.csv`

### 2. Data Analysis (SQL)
Loaded the cleaned data into a database and answered 10 business questions using `GROUP BY`, `HAVING`, subqueries, CTEs, `CASE WHEN`, and window functions (`DENSE_RANK`).

| # | Business Question |
|---|---|
| 1 | Total revenue by male vs. female customers |
| 2 | Customers who used a discount but still spent above the average |
| 3 | Top 5 states by average purchase amount (min. 70 purchases) |
| 4 | Average purchase amount by shipping type |
| 5 | Do subscribers spend more than non-subscribers? |
| 6 | Top 5 products with the highest discount rate |
| 7 | Customer segments: New, Returning, Loyal |
| 8 | Top 3 most purchased products within each category |
| 9 | Are repeat buyers more likely to subscribe? |
| 10 | Revenue contribution by age group |

### 3. Dashboard (Power BI)
Built an interactive dashboard on the cleaned dataset (see below).

---

## 📊 Dashboards

The Power BI dashboard (`customer_shopping_behaviour.pbix`) includes:

- **KPI card** – total number of customers
- **Purchase Amount by Category** and **Total Items by Category** – column charts
- **Purchase Amount by Age Group** and **Total Items by Age Group** – bar charts
- **% of Customers by Subscription Status** – donut chart
- **Slicers** – filter by Gender, Subscription Status, and Category

> 💡 *Tip: add a screenshot of your dashboard to an `images/` folder and display it here:*
> `![Dashboard](images/dashboard.png)`

---

## 📈 Results

- **Total revenue:** ~$233K, with an average purchase of ~$59.76
- **Gender:** Male customers generated about **$157.9K (68%)** of revenue vs. **$75.2K** from female customers
- **Category:** Clothing is the top revenue driver (~$104K), followed by Accessories (~$74K), Footwear (~$36K), and Outerwear (~$18.5K)
- **Subscriptions:** Subscribers and non-subscribers spend almost the same on average (~$59.5 vs. ~$59.9), and only about 27% of customers are subscribed, so subscription is a growth opportunity rather than a spending driver
- **Shipping:** Average spend is similar across shipping types ($58.5–$60.7); 2-Day Shipping and Express are slightly higher
- **Top states by average spend (70+ purchases):** Alaska, Pennsylvania, West Virginia, Nevada, Washington
- **Discounts:** Hat, Sneakers, Coat, Sweater, and Pants have the highest discount rates (~47–50% of their purchases)
- **Age groups:** Revenue is spread fairly evenly (about 24–27% each), with Young-Adults contributing the most
- **Loyalty:** Most customers have more than 20 previous purchases, showing a strong repeat-customer base

**Business recommendations**
1. Promote subscriptions to loyal, high-frequency customers, since they already buy often
2. Target female customers with campaigns to close the revenue gap
3. Review discount strategy on the most-discounted products to protect margins
4. Focus marketing on high-spend states and the Clothing category

---

## ▶️ How to Run

**1. Clone the repository**
```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

**2. Data cleaning (Python)**
```bash
pip install pandas jupyter
jupyter notebook customer_shopping_behaviour.ipynb
```
Run all cells. This reads `customer_shopping_behavior.csv` and generates `customer_shopping_behavior_clean.csv`.

**3. SQL analysis**
- Import `customer_shopping_behavior_clean.csv` into your database as a table named `customer_shopping_behavior_clean`
- Open and run `customer_shopping_behaviour.sql`

**4. Dashboard**
- Open `customer_shopping_behaviour.pbix` in **Power BI Desktop**

---

## 📁 Project Structure

```
├── customer_shopping_behavior.csv          # Raw dataset
├── customer_shopping_behavior_clean.csv    # Cleaned dataset
├── customer_shopping_behaviour.ipynb       # Python cleaning notebook
├── customer_shopping_behaviour.sql         # SQL queries (10 business questions)
├── customer_shopping_behaviour.pbix        # Power BI dashboard
└── README.md
```

---

## 👤 Author

**Arun**
📍 India
🔗 *Add your LinkedIn / Portfolio link here*
