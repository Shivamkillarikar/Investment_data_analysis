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
### Insights and Analysis
-**Majority of the monthly Investments are done in Mutual Funds and Stocks, the reason for this is for their personal saving and wealth generation. Both stocks and Mutual Funds offer higher returns during these 10 years after which it starts declining the forecast shows it might increase in 20th year.**

-**Around 66 percent of high income people invested in real estate which has given them linear returns. The dominant reason for investement in real estate is building their own homes/Buying a new car followed by tax saving and wealth generation**

-**On the other hand in crypto currency the longer the duration the more less is the ROI. Only High income people invested in crypto currency the reason for their investment is child education/marriage**

-**Bank-FD,RD has given consistent profits with people from all income roup investing. The reason for this investing includes personal savings,child education/marriage, ..etc**

-**Primary reasons for investment are personal savings and wealth generation**

-**Combination of mutual funds and Stocks has provided the maximum investment value of around 10 Million within 10 years**

-**People are motivated to invest due to motivation from friends and family members**

## Conclusion
This analysis provides actionable insights into investment behavior and performance, helping stakeholders make informed decisions.

---

### Repository
Explore the project and code in detail here: [GitHub Repository Link](#)

---

Let me know if you’d like further tweaks!
