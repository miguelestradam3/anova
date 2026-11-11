# Hypothesis Testing & ANOVA with Python

This project demonstrates a complete data analysis pipeline using Python to perform hypothesis testing, Ordinary Least Squares (OLS) regression, one-way Analysis of Variance (ANOVA), and post-hoc pairwise comparisons on historical marketing promotion data.

---

## **Project Overview**
The objective of this analysis is to determine whether product sales differ significantly across various marketing promotion categories (specifically **TV** budgets and **Influencer** sizes) to help stakeholders make data-driven budget allocations.

---

## **Key Steps & Workflow**

### **1. Data Import & Libraries**
We utilize standard, trusted Python libraries for data manipulation, visualization, and statistical modeling:
* `pandas`: For data loading and preprocessing.
* `matplotlib` & `seaborn`: For exploratory data visualization (boxplots, residual plots).
* `statsmodels`: For OLS regression modeling, assumption checking, and one-way ANOVA calculations.
* `statsmodels.stats.multicomp`: For Tukey’s HSD post-hoc testing.

### **2. Exploratory Data Analysis (EDA)**
* Visualized sales distribution across categorical features using Seaborn boxplots (`sns.boxplot`).
* Identified that `TV` budget categories (`Low`, `Medium`, `High`) exhibit strong variance in sales, whereas `Influencer` sizes show minimal variation.
* Cleaned the dataset by dropping missing values (`dropna()`) and validating data integrity.

### **3. Linear Regression & Assumption Checks**
* **OLS Model:** Fitted a linear regression model predicting `Sales` based on the categorical variable `TV`:
  $$\text{Sales} \sim C(\text{TV})$$
* **Model Performance:** Achieved an $R^2$ of **0.874**, indicating that $87.4\%$ of the variation in sales can be explained by the TV promotion budget.
* **Diagnostics:** Checked linear regression assumptions:
  * **Normality:** Evaluated using residual histograms and Normal Q-Q plots.
  * **Homoscedasticity:** Verified constant variance via a **Fitted Values vs. Residuals** scatter plot.

### **4. Hypothesis Testing (One-Way ANOVA)**
To test whether population means differ across TV budget tiers:
* **Null Hypothesis ($H_0$):** $\mu_{\text{High}} = \mu_{\text{Medium}} = \mu_{\text{Low}}$ (No difference in mean sales across groups).
* **Alternative Hypothesis ($H_A$):** At least one group mean is significantly different.
* **Result:** The ANOVA test yielded an extremely small p-value ($p \approx 8.81 \times 10^{-256}$), leading to the rejection of the null hypothesis.

### **5. Post-Hoc Analysis (Tukey's HSD)**
Since the ANOVA test confirmed significant differences, **Tukey’s Honestly Significant Difference (HSD)** test was performed to control the family-wise error rate while comparing all group pairs:
* **High vs. Low TV:** Significant difference (~$208.81M difference in sales).
* **High vs. Medium TV:** Significant difference (~$101.51M difference in sales).
* **Medium vs. Low TV:** Significant difference (~$107.31M difference in sales).

---

## **Business Recommendations & Key Takeaways**
1. **High TV Budgets Win:** High TV promotion budgets generate significantly higher sales than Medium and Low tiers.
2. **Actionable Insight:** Stakeholders should prioritize allocating marketing funds toward high-tier TV campaigns to maximize expected revenue returns.
3. **Robust Methodology:** Combining OLS regression, ANOVA, and Tukey's HSD provides a rigorous, statistically sound framework for evaluating categorical group differences without inflating Type I error rates.

---

## **Reference Dataset**
* Dataset: *Dummy Marketing and Sales Data* (Kaggle / H.S. Saragih).