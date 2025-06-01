# Project Title  
**Who Pays More? Machine Learning and Data-Driven Insights into Pricing, Profiling, and Privacy in E-Commerce**

## Summary  
This project explores whether customers identified as high spenders are consistently charged higher prices for the same products on an e-commerce platform. Using statistical analysis and machine learning, we uncover whether behavioral profiling leads to unfair pricing.

---

## :compass: Complete Project Roadmap

### 1. :inbox_tray: Data Collection & Preparation  
**Objective**: Combine user behavior and transaction data to understand how different customers are charged.

**Datasets Used**:
- `user_profiles`: customer_id, avg_spend, total_orders, state
- `combined_data`: customer_id, payment_value, product_category, payment_type

**Steps**:
- Merged datasets using `customer_id`
- Created `risk_group` label:
  - **High risk**: avg_spend > 100  
  - **Low risk**: avg_spend ≤ 100

**Tools**: Python (`pandas`)

---

### 2. :bar_chart: Exploratory Analysis  
**Goal**: Identify initial patterns in spending and pricing by user group.

**Findings**:
- High-risk users pay significantly more on average  
- Price differences exist across many product categories

**Visuals Created (Python)**:
- Bar charts comparing average payment by category and risk group  
- Histograms showing distribution of payments  

---

### 3. :test_tube: Statistical Testing  
**Objective**: Validate whether pricing differences are statistically significant.

**Tests Performed**:
- **Welch’s t-test** for comparing average `payment_value` between groups  
- **Chi-square test** on binned price levels  

**Conclusion**:  
- Pricing gaps are **highly significant** — not due to chance

---

### 4. :closed_lock_with_key: Privacy and Fairness Framing  
- Pricing is influenced by behavioral data without user knowledge  
- Raises issues under **GDPR**, **CCPA**, and **AI ethics** guidelines  
- Economic discrimination may occur unintentionally  

> “Behavioral data is being used not just to predict — but to charge.”

---

### 5. :robot_face: Machine Learning: Pricing Influence Modeling  

#### A. Regression Task: Predict `payment_value`  
- **Model**: Random Forest Regressor  
- **Features**: `product_category`, `payment_type`, `review_score`, `payment_installments`, `risk_group`  
- **Target**: `payment_value`

**Steps**:
- Encoded categorical variables  
- Trained and tested the model  
- Evaluated using **RMSE** and **R²**

#### B. Fairness Audit  
- Used **feature importance** to detect influence of `risk_group`  
- Found `risk_group` to be a top predictor of price

#### C. Privacy Check  
- Compared two models: one with `risk_group`, one without  
- Model without `risk_group` performed worse → **evidence of profiling**

---

### 6. :drawing_pin: Conclusion & Recommendations  

**Findings**:
- High-risk users consistently pay more  
- Pricing models can learn and amplify bias  
- Users likely unaware of how their behavior affects pricing  

**Recommendations**:

| Area         | Recommendation                                      |
|--------------|------------------------------------------------------|
| Transparency | Disclose when pricing uses behavioral data           |
| Fairness     | Limit pricing variation between user profiles        |
| Control      | Allow users to opt out of personalized pricing       |
| Auditing     | Regularly test models for hidden bias                |

---

### ✅ Final Deliverables

| Component         | Tool             | Purpose                                           |
|------------------|------------------|---------------------------------------------------|
| Data processing   | Python (pandas)  | Clean, merge, and feature engineer                |
| Statistical tests | `scipy.stats`    | Validate pricing differences across user groups   |
| ML modeling       | `scikit-learn`   | Identify what drives pricing and model behavior   |
| Visualization     | matplotlib       | Show pricing gaps and feature influence           |
| Reporting         | Markdown/Slides  | Link findings to real-world privacy concerns      |
