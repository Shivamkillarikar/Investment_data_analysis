Here’s a properly formatted version of your README content for GitHub, following Markdown best practices for readability:

---

# Investment Data Analysis

## Objective
The primary goal of this project is to analyze and evaluate investment performance using various financial metrics, including monthly contributions, overall investment value, returns, and more.

---

## Data Sources
The dataset is sourced from Kaggle and includes the following key columns:

- **Age**: Age of the person who is investing.
- **Duration to Save**: The time period for which the investment will be made.
- **Annual Income**: Yearly income of the investor.
- **Gender**: Gender of the investor (Male or Female).
- **High_or_low**: 
  - A DAX measure that categorizes annual income.
  - Income > ₹2,50,000 is categorized as **"👆High"**, and income < ₹2,50,000 is categorized as **"👇Low"**.
  
- **Investment_per_month**: Monthly investment amount.

---

## DAX Measures

### **Investment_Value**
Calculates the total investment value based on monthly contributions and duration to save.

**Formula**:
```DAX
Investment_Value = 
SUMX(
    investment_data, 
    (investment_data[Investment_per_month] * 12 * investment_data[Duration_to_save(in_Years)]) + 
    (investment_data[Investment_per_month] * 12 * 0.15 * investment_data[Duration_to_save(in_Years)])
)
```

---

### **Return Indicator**
Categorizes Return on Investment (ROI) as either **high** (`"🟢↑"`) or **low** (`"🔴↓"`). 
- ROI > 20% is considered **high**.
- ROI ≤ 20% is considered **low**.

**Formula**:
```DAX
Return_Indicator = 
IF(
    DIVIDE(
        [Investment_Value] - SUM(investment_data[Investment_per_month]) * SUM(investment_data[Duration_to_save(in_Years)]), 
        SUM(investment_data[Investment_per_month]) * SUM(investment_data[Duration_to_save(in_Years)]),
        0
    ) > 0.2, 
    "🟢↑", 
    "🔴↓"
)
```

---

### **Working_or_not**
Categorizes whether an investor is a working professional.

- **👍** for working professionals.
- **👎** for non-working professionals.

**Formula**:
```DAX
Working_or_not = 
IF('investment_data'[Working_professional] = "True", "👍", "👎")
```

---

## Additional Columns and Measures

- **Mode of Investment**: The method of investment, such as cryptocurrency, fixed deposits, mutual funds, stocks, etc.
- **Working_professional**: Indicator column to identify if the investor is a working professional.

---

### Visualizations and Insights
- **Income Categorization**: Categorizes investors based on their annual income.
- **Return Indicators**: Helps visualize and understand investment performance.
- **Dynamic Filters**: Interactive visuals for exploring investment data by age, gender, income, and duration.

---

## Conclusion
This analysis provides actionable insights into investment behavior and performance, helping stakeholders make informed decisions.

---

### Repository
Explore the project and code in detail here: [GitHub Repository Link](#)

---

Let me know if you’d like further tweaks!
