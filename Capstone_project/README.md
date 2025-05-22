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

### 1) Exploratory Data Analysis (EDA) reveals:
### 1.1) Descriptive Statistics

 [Add figure]  


 
✍🏻 _I examined the dataset using statistical methods and gained critical insights:_
* **Satisfaction level** scores a **moderate average (0.61)**, but **25% of employees** report **low satisfaction** (<= 0.44)
* **Last Evaluation** achieves a **high mean of 0.72**, suggesting **strong overall performance**
* **Number of Projects** averages **around 4**, while some employees handle up to **7 projects max**
* **Average Monthly Hours** range widely from **96 to 310**, while typical full-time hours fall 160-180 hours/month, suggesting **overwork** for some employees
* **Time Spent at Company** averages **3.5 years**, some employees staying **up to 10 years**
* **Work Accidents** occurred in about **14.5% of cases**, which is **relatively frequent**
* **Attrition Rate** is **high at 23.8%**, meaning **1 in 4 employees left**
* **Promotions in the Last 5 Years** are **very rare (2.1%)**, pointing to **limited career growth**.
  
    
### 1.2) Data Exploration (continue EDA)

[ add figure]


  * **~83% of employees staying**
  * **~17% of employees left**
    
### 1.3) Data visualization

 [ADD PLOT]

 
_Ratio plot also shows the same findings:_

  **83% staying, 17% left**


---

### 2) Relationship between ```average_monthly_hours``` and ```promotion_last_5years```


 [ADD PLOT]


 
 ✍🏻 **Categorical scatter plot** shows:
  * Blue dominated on Top row--> **Most promoted employees stayed, very few promoted left**
  * On the far right, most dots appear on the bottom row--> **High-hour workers were rarely promoted**
  * Orange toward right end--> **Leavers worked the longest hours, eventually left**


  
 ---

 ### 3) Correlation Heatmap

_Correlation Heatmap shows how strong variables are related to each other, gives a number from:_
* **1** (strongly go up together)
* **0** (no relation)
* **-1** (one goes up, other goes down)
  
 [add Heatmap]


 #### Key Insights:
- **Satisfaction and Leaving:** The darker box with **-0.39** means people who are **less satisfied are more likely to leave** the company.

- **Projects and Hours:** The box with **0.42** means if someone has **more projects**, they also usually work **more hours**.

- **Evaluation and Projects:** With a score of **0.35**, people with **better performance** evaluations often **get more projects**.

- **Leaving and Work Accidents:** A weak score of **-0.15** means people who **had an accident are less likely to leave**, but it's not very strong.

- **Promotions and Leaving**: A tiny number **-0.06** means promotions and leaving the job **aren’t really connected**.

- **Most other boxes are light-colored**, which means **many things aren’t strongly related**.

✍🏻 *People who work on more projects usually work more hours and get better performance scores. Also, people who are not happy at work are more likely to quit.*

---


### 4) Logistic Regression

