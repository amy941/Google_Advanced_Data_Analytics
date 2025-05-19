I'm working on it :)

# Forecasting Employee Turnover Rates & What Causes It

## Goal
- Providing HR with insights into why employees leave the company.

## Business Understanding
- HR department at Salifort Motors is looking for ways to boost employee satisfaction. They want data to help answer: _“What factors lead employees to leave the company?”_
  
**- Tasks:**
  * Analyze data 
  * Build a model to predict whether an employee is likely to leave.

## Data Understanding
Google provided datasets for a fictional company called "Salifort Motors". The data includes about 12,000 employees, each with 9 features related to satisfaction level, performance evaluation, salary, company history, department, and contributed projects.

- **Exploratory Data Analysis (EDA)** reveals:
  * **~83% of employees staying**
  * **~17% of employees left**
    
- **Ratio plot** also shows the same findings: 83% staying, 17% left

  [ADD PLOT]


- Relationship between ```average_monthly_hours``` and ```promotion_last_5years```
  
  **Categorical scatter plot** shows:
  * Blue dominated on Top row--> **Most promoted employees stayed, very few promoted left**
  * On the far right, most dots appear on the bottom row--> **High-hour workers were rarely promoted**
  * Orange toward right end--> **Leavers worked the longest hours, eventually left**


  
 [ADD PLOT]
