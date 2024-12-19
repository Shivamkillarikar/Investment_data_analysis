### Investment Data Analysis
Objective
The primary goal of this project is to analyze and evaluate investment performance using various financial metrics, including monthly contributions, overall investment value,returns...etc

## Data Sources
The dataset is sourced from kaggle, which includes the following key columns:

Age: Age of the person who is investing
Duration to Save: Until how much time you want to invest
Annual Income:Yearly Income
Gender:Male or Female
## High_or_low: It's a DAX measure to categorize annual income> 2,50,000 as "👆High" and income<2,50,000 as "👇Low"
Investment_per_month: Monthly investment amount.
## Investment_Value= DAX measure to calculate the investment value based on monthly investment and duration to save
# Formula
Investment_Value = 
SUMX(
    investment_data, 
    (investment_data[Investment_per_month] * 12 * investment_data[Duration_to_save(in_Years) ]) + 
    (investment_data[Investment_per_month] * 12 * 0.15 * investment_data[Duration_to_save(in_Years) ])
)
Mode of Investment: Various methods of investment like crypto currency,fd,mutual funds,stocks..etc
## Return Indicator: A DAX measure to categorize Return on investment as high "🟢↑" or low "🔴↓". ROI of above 20 percent is considered high else low
# Formula
Return_Indicator = 
IF(
    DIVIDE(
        [Investment_Value] - SUM(investment_data[Investment_per_month]) * SUM(investment_data[Duration_to_save(in_Years) ]), 
        SUM(investment_data[Investment_per_month]) * SUM(investment_data[Duration_to_save(in_Years) ]),
        0
    ) > 0.2, 
    "🟢↑", 
    IF(
        DIVIDE(
            [Investment_Value] - SUM(investment_data[Investment_per_month]) * SUM(investment_data[Duration_to_save(in_Years) ]), 
            SUM(investment_data[Investment_per_month]) * SUM(investment_data[Duration_to_save(in_Years) ]),
            0
        ) < 0.2, 
        "🔴↓", 
        "-"
    )
)
## Working_or_not: A DAX measure to Categorize working professional as "👍" and non-working professional as  "👎"
Working_professional: Indicator of whether the investor is a working professional.


