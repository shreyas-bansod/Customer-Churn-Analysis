# Customer Churn Analysis

## 📌 Project Overview

Customer churn is a major business problem because losing existing customers can reduce recurring revenue and increase customer acquisition costs.

This project analyzes customer churn using the **Telco Customer Churn dataset** to identify customer characteristics associated with higher churn and translate the findings into actionable business recommendations.

The analysis follows a complete Data Analyst workflow:

**Data Cleaning → Exploratory Data Analysis → Customer Segmentation → Statistical Analysis → Visualization → Business Recommendations**

---

## 🎯 Business Objective

The main objectives of this project are to:

* Measure the overall customer churn rate
* Identify customer segments with higher churn
* Analyze the relationship between churn and customer characteristics
* Statistically validate important categorical relationships
* Analyze differences in monthly charges between churned and retained customers
* Identify an actionable high-risk customer segment
* Provide data-driven recommendations for customer retention

---

## 📊 Dataset

**Dataset:** Telco Customer Churn

The dataset contains information about customer demographics, services, contracts, payment methods, tenure, charges, and churn status.

Key variables include:

* Customer ID
* Gender
* Senior Citizen
* Partner
* Dependents
* Tenure
* Internet Service
* Online Security
* Tech Support
* Contract
* Payment Method
* Monthly Charges
* Total Charges
* Churn

---

## 🛠️ Tools & Technologies

* **Python**
* **Pandas** — data manipulation and analysis
* **NumPy** — numerical operations
* **Matplotlib** — data visualization
* **Seaborn** — statistical visualization
* **SciPy** — statistical hypothesis testing
* **Jupyter Notebook**

---

## 🧹 Data Cleaning

The dataset was inspected for:

* Missing values
* Duplicate records
* Incorrect data types
* Inconsistent values

### Total Charges

`TotalCharges` was initially stored as an object/string column.

It contained 11 blank values. These corresponded to customers with zero tenure, so the values were converted to numeric and represented as `0`.

After cleaning:

* No missing values remained
* No duplicate records were found
* `TotalCharges` was converted to a numeric data type

---

## 📈 Exploratory Data Analysis

### Overall Churn

The overall churn rate was:

**26.54%**

This means approximately one in four customers in the dataset had churned.

### Contract Type

| Contract       | Churn Rate |
| -------------- | ---------: |
| Month-to-month | **42.71%** |
| One year       |     11.27% |
| Two year       |      2.83% |

Month-to-month customers showed substantially higher observed churn than customers on longer contracts.

### Tenure

| Tenure Group | Churn Rate |
| ------------ | ---------: |
| 0–12 months  | **47.44%** |
| 13–24 months |     28.71% |
| 25–48 months |     20.39% |
| 49–60 months |     14.42% |
| 61–72 months |  **6.61%** |

Churn decreased substantially across the observed tenure groups.

### Payment Method

| Payment Method   | Churn Rate |
| ---------------- | ---------: |
| Electronic check | **45.29%** |
| Mailed check     |     19.11% |
| Bank transfer    |     16.71% |
| Credit card      |     15.24% |

Electronic check customers showed the highest observed churn rate.

### Internet Service

| Internet Service    | Churn Rate |
| ------------------- | ---------: |
| Fiber optic         | **41.89%** |
| DSL                 |     18.96% |
| No internet service |      7.40% |

Fiber optic customers showed substantially higher observed churn than the other groups.

---

## 🔎 Customer Segmentation

A deeper segmentation analysis was performed by combining **contract type and tenure**.

The highest-volume high-churn segment was:

**Month-to-month + 0–12 months**

* Customers: **1,994**
* Churned: **1,024**
* Churn rate: **51.35%**

This segment represents approximately **28.3% of the entire customer base**.

Further analysis showed that within this segment:

* Electronic check → **63.10% churn**
* Fiber optic → **70.20% churn**

The most specific high-risk combination identified was:

### Month-to-month + 0–12 months + Fiber optic + Electronic check

* Customers: **631**
* Churned: **449**
* Churn rate: **71.16%**

This segment was selected as an important focus area because it combines a high churn rate with substantial customer volume.

---

## 📐 Statistical Analysis

Chi-square tests were used to evaluate associations between categorical variables and churn.

### Results

| Variable         | Chi-square |       P-value |
| ---------------- | ---------: | ------------: |
| Contract         |    1184.60 | 5.86 × 10⁻²⁵⁸ |
| Tenure Group     |     872.47 | 1.53 × 10⁻¹⁸⁷ |
| Payment Method   |     648.14 | 3.68 × 10⁻¹⁴⁰ |
| Internet Service |     732.31 | 9.57 × 10⁻¹⁶⁰ |

All four relationships were statistically significant at the 5% significance level.

A two-sample t-test was also used to compare monthly charges between churned and retained customers.

### Monthly Charges

| Customer Group | Average Monthly Charges |
| -------------- | ----------------------: |
| Retained       |                  $61.27 |
| Churned        |              **$74.44** |

The t-test produced:

**t-statistic = 18.41**

**p-value = 8.59 × 10⁻⁷³**

This indicates a statistically significant difference in monthly charges between the two groups.

> Statistical significance indicates association or difference in the observed data; it does not by itself establish causation.

---

## 💡 Key Business Insights

1. **Month-to-month customers have substantially higher observed churn** than customers on one- or two-year contracts.

2. **Early-tenure customers are a major risk area**, with the highest churn observed during the first 12 months.

3. **Electronic check customers show elevated churn**, making the payment experience an area worth investigating.

4. **Fiber optic customers show elevated churn**, particularly within the early-tenure month-to-month segment.

5. The most actionable segment identified was **month-to-month, 0–12 month, fiber optic customers using electronic check**, with a **71.16% observed churn rate**.

6. Churned customers have **higher average monthly charges** than retained customers, suggesting that pricing or service configuration should be investigated alongside other customer characteristics.

---

## 🎯 Business Recommendations

### 1. Focus on early-tenure retention

Investigate onboarding, early customer engagement, support interactions, and service experience during the first 12 months.

### 2. Investigate month-to-month customers

Evaluate whether appropriate contract options, incentives, or engagement strategies could improve retention.

### 3. Investigate the Fiber optic customer experience

Analyze pricing, service expectations, technical issues, and support experience to understand the elevated churn pattern.

### 4. Review the electronic-check payment experience

Investigate billing communication and payment experience and evaluate whether alternative payment options improve customer retention.

### 5. Prioritize the identified high-risk segment

Use the identified segment for targeted retention experiments and further investigation:

**Month-to-month + 0–12 months + Fiber optic + Electronic check**

The analysis identifies an important association; it does not establish that any individual factor directly causes churn.

---

## 📌 Business Impact

The analysis demonstrates how customer-level data can be transformed into actionable retention insights.

Instead of treating all customers as equally likely to churn, businesses can use segmentation to identify groups with substantially different observed churn rates and prioritize further investigation and retention efforts.

---

## 📁 Project Structure

```text
Customer-Churn-Analysis/
│
├── Customer_Churn_Analysis.ipynb
├── data/
│   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
│
└── README.md
```

---

## 🚀 Skills Demonstrated

* Data Cleaning
* Exploratory Data Analysis
* Data Transformation
* Customer Segmentation
* Statistical Hypothesis Testing
* Categorical Analysis
* Numerical Analysis
* Data Visualization
* Business Insight Generation
* Data-Driven Recommendations

---

## 👤 Project Summary

This project demonstrates an end-to-end customer churn analysis using Python, combining exploratory analysis, statistical testing, segmentation, and business interpretation to identify customer groups associated with elevated churn and translate those findings into practical retention recommendations.
