# Forecasting Employee Turnover: Causes & Insights 📉

## Goal 🎯
- Providing HR with insights into why employees leave the company.

## Business Understanding 💼
- HR department at Salifort Motors is looking for ways to boost employee satisfaction. They want data to help answer: _“What factors lead employees to leave the company?”_
  
**- Tasks:**
  * Analyze data 
  * Build a model to predict whether an employee is likely to leave.

## Data Understanding 📊
Google provided datasets for a fictional company called "Salifort Motors". The data includes about 12,000 employees, each with 9 features related to ```satisfaction level```, ```performance evaluation```, ```salary```, ```company history```, ```department```, and ```number of projects```.

### 1) Exploratory Data Analysis (EDA) reveals:
### 1.1) Descriptive Statistics

![descriptive](https://github.com/user-attachments/assets/9d7fd857-47b8-4487-8ccf-d6945091f9c1)

 
✍🏻 _I examined the dataset using statistical methods and gained critical insights:_
* **Satisfaction level** scores a **moderate average (0.61)**, but **25% of employees** report **low satisfaction** (<= 0.44)
* **Last Evaluation** achieves a **high mean of 0.72**, suggesting **strong overall performance**
* **Number of Projects** averages **around 4**, while some employees handle up to **7 projects max**
* **Average Monthly Hours** range widely from **96 to 310**, while typical full-time hours fall between 160-180 hours/month, suggesting **overwork** for some employees
* **Time Spent at Company** averages **3.5 years**, some employees staying **up to 10 years**
* **Work Accidents** occurred in about **14.5% of cases**, which is **relatively frequent**
* **Attrition Rate** is **high at 23.8%**, meaning **1 in 4 employees left**
* **Promotions in the Last 5 Years** are **very rare (2.1%)**, pointing to **limited career growth**.
  
    
### 1.2) Data Exploration (continue EDA)
```
print('Number of people who left: ')
print(df1['left'].value_counts())

print('\nPercentage of people who left: ')
print(df1['left'].value_counts(normalize=True)*100)
```

![EDA](https://github.com/user-attachments/assets/2f619f8c-20d0-40e0-89e6-0c335c888f0e)


✍🏻 **~83% of employees staying, ~17% of employees left**
    
### 1.3) Data visualization

![ratio_plot](https://github.com/user-attachments/assets/ed00ed12-ec15-4641-9107-6ec3cb03bc16)

 
✍🏻 _Ratio plot also shows the same findings:_
  **83% staying, 17% left**

👉 For more details, visit: [Salifort_Motors_project](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/Capstone_project/20250418_Salifort%20Motors%20project%20lab.ipynb)

---

### 2) Relationship between ```average_monthly_hours``` and ```promotion_last_5years```

![scatter_plot](https://github.com/user-attachments/assets/c94e1e3f-80f5-41cf-84f3-049e96afdaf0)
 
 ✍🏻 **Categorical scatter plot** shows:
  * Blue dominated on Top row--> **Most promoted employees stayed, very few promoted left**
  * On the far right, most dots appear on the bottom row--> **High-hour workers were rarely promoted**
  * Orange toward right end--> **Leavers worked the longest hours, eventually left**


👉 For more details, visit: [Salifort_Motors_project](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/Capstone_project/20250418_Salifort%20Motors%20project%20lab.ipynb)
---

 ### 3) Correlation Heatmap

_Correlation Heatmap shows how strong variables are related to each other, gives a number from:_
* **1** (strongly go up together) ⬆️⬆️
* **0** (no relation) ❌
* **-1** (one goes up, other goes down) ⬆️⬇️
  
![heatmap](https://github.com/user-attachments/assets/2fb2edb9-1de4-412e-b723-f6be895f7555)


 ### Key Insights 
- **Satisfaction and Leaving:** The box with **-0.39** means people who are **less satisfied are more likely to leave** the company ⬆️⬇️

- **Projects and Hours:** The box with **0.42** means if someone has **more projects**, they also usually work **more hours** ⬆️⬆️

- **Evaluation and Projects:** With a score of **0.35**, people with **better performance** evaluations often **get more projects** ⬆️⬆️

- **Leaving and Work Accidents:** A weak score of **-0.15** means people who **had an accident are less likely to leave** ⬆️⬇️

- **Promotions and Leaving**: A tiny number **-0.06** means promotions and leaving the job **aren’t really connected** ❌

- **Most other boxes are light-colored**, which means **many things aren’t strongly related** ❌

### Conclusions 
- People who work on **more projects** usually **work longer hours** and get **better performance scores**.
- People who are assigned **more projects** tend to be **unhappy** at work and more **likely to quit**.

👉 For more details, visit: [Salifort_Motors_project](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/Capstone_project/20250418_Salifort%20Motors%20project%20lab.ipynb)

---

### 4) Logistic Regression
### 4.1) Heatmap (after dummy encoding ```department```)

_Correlation score between -1 and 1:_
* **1** = very strong connection (go up together) ⬆️⬆️
* **0** = no connection ❌
* **-1** = opposite connection (one up, one down) ⬆️⬇️

![heatmap_2](https://github.com/user-attachments/assets/4c77f062-b97f-418d-a4c8-4a78c9a9ae82)

### Key Insights 

- **Number of Projects & Monthly Hours: 0.33**
→ People who do **more projects** also work **more hours** ⬆️⬆️

- **Evaluation & Number of Projects: 0.27**
→ People with **better evaluations** tend to have **more projects** ⬆️⬆️

- **Evaluation & Monthly Hours: 0.26**
→ **Better performers** also tend to work **more hours** ⬆️⬆️

- **Satisfaction & Tenure (Years at Company): -0.15**
→ People who **stay longer** may be slightly **less satisfied** ⬆️⬇️

- **Satisfaction & Projects: -0.13**
→ **More projects** might mean a little **less happiness** ⬆️⬇️

- **Satisfaction & Monthly Hours: -0.0063**
→ Almost **no link** between happiness and working long hours ❌

- **Evaluation & Tenure: 0.097**
→ A **tiny connection** between experience and performance ❌

### Conclusions 
- People with **more projects** usually **work more hours** and **perform better**.
- There’s **no strong link** between how **happy** people are and how much they **work**.
- **Staying longer** at the company might make some people a bit **less satisfied**.

👉 For more details, visit: [Salifort_Motors_project](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/Capstone_project/20250418_Salifort%20Motors%20project%20lab.ipynb)

---

### 4.2) Confusion Matrix
- **Confusion Matrix** acts like a **scoreboard** that predicts:
  * ✅"How many times the model guessed correctly?"
  * ❌"How many times it got wrong?"

![confusion_matrix](https://github.com/user-attachments/assets/a39b37f1-817c-4772-8597-2dac9f2bc106)

### Key Insights 
- **Top left (True Negatives):** 2165 people **stayed**, computer guessed they would **stay**. Yay, correct guess! ✅
- **Top right (False Positives):** 156 people **stayed**, but computer wrongly guessed they would **leave**. Oops! ❌
- **Bottom left (False Negatives):** 348 people **left**, but computer guessed they would **stay**. Oops! ❌
- **Bottom right (True Positives):** 123 people **left**, and computer guessed they would **leave**. Yay! ✅

### Conclusions 
- **If the computer was perfect**, it would only make correct guesses --> in **Top left** and **Bottom right**
- The **model is good at finding people who stay**, not who leave
- The model **needs improvement** in predicting leavers

👉 For more details, visit: [Salifort_Motors_project](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/Capstone_project/20250418_Salifort%20Motors%20project%20lab.ipynb)

---

### 5) Recall evaluation metrics

```
target_names = ['Predicted would not leave', 'Predicted would leave']
print(classification_report(y_test, y_pred, target_names=target_names))
```

![recall_metrics](https://github.com/user-attachments/assets/efac011a-cb82-4212-9e3a-e05c890c2002)

### Key Insights 
The Logistic Regression model achieved:
- Precision of 79%,
- Recall of 82%,
- F1-score of 80%,
- Accuracy of 82%,
- AUC score of 89%.

### Conclusions 
- Logistic Regression model looks **pretty good overall** with 82% Accuracy
- However, the **model isn't as good** when predicting employees who **leave**, scores significantly lower

👉 For more details, visit: [Salifort_Motors_project](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/Capstone_project/20250418_Salifort%20Motors%20project%20lab.ipynb)

---

## Results & Evaluation 🤝
1) Employees with **more projects**, will **overwork**, and get **better performance scores**.
2) Employees with **more projects**, are **unhappy**, and more likely to **leave**.
3) **No strong connection** between **working hours** and employee **satisfaction**.
4) **Longer tenure** is slightly associated with **lower satisfaction** over time.
5) **Logistic Regression model works well for stayers**, but not leavers.
