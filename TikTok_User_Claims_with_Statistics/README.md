# OVERVIEW:
Little did I know that Statistics is the backbone in data 😅 In this end-of-course project, I tackled 2 different case studies using Python and basic Stats to solve:
- *Case Study 1:* **Automatidata,** a fictional data consulting firm
- *Case Study 2:* **TikTok,** a short-form video hosting firm

# Case Study 1: Automatidata 🚕
## Link here: [Case_study_1: Automatidata](https://github.com/amy941/Google_Advanced_Module-4_Statistics/blob/main/Case_Study_1_%20Automatidata.ipynb)

## Scenario: 
New York taxi and Limousine Commission (TLC) has approached the data consulting firm Automatidata to develop an app that enables TLC riders to estimate the taxi fares in advance of their ride. TLC reached out to data team at Automatidata to assist them answer these key questions:
- Is there a relationship between fare amount and payment type?
- Do customers who use credit card pay higher fare amounts than customers who use cash?
- What sort of payment would help increase revenue for cab drivers?
  
At the end of this project, TLC will get actionable insights on how to enhance rider and driver experiences while optimizing revenue generation. 

## What I Learned:
  
**1) Compute a descriptive stats:**
First, take a glimpse at the big data to understand how the dataset is structured before proceeding. The following functions are used:

**pandas:** .describe(), .head(), .shape | **numpy:** .mean()

 ```python
 taxi_data.describe(include='all')
 ```

![describe()](https://github.com/user-attachments/assets/9b3dcf70-2f0c-41a5-9a3a-80af6de01a19)

✍ *.describe()* generates the table with basic descriptive stats: mean, std deviation, min/max, interquartile, etc.
     
```python
taxi_data.groupby('payment_type')['fare_amount'].mean()
```
✍ Use *.groupby()* and *.mean()* to compute the mean value of **fare_amount(price)** for each group of **payment_type** (credit card, cash,...) in the sample data.

![avg mean](https://github.com/user-attachments/assets/1c9d15bb-1da5-43a8-816d-22337b4468da)   

✍*1-Credit card, 2-Cash, 3-No charge, 4: Dispute, 5-Unknown*
   
We're interested in payment_type: 1-Credit card and 2-Cash. **The table shows credit card users tend to pay more than cash users**, $13.4 and $12.2, respectively.     

 ---
 
**2) Conduct Hypothesis test and A/B test:**

```python
credit_card = taxi_data[taxi_data['payment_type'] == 1]['fare_amount'] 
cash = taxi_data[taxi_data['payment_type'] == 2]['fare_amount']
```
✍ Firstly, assigned variables, one for Credit Card and one for Cash.

Then, created **BOOLEAN** ```taxi_data['payment_type'] == 1``` checks if the payment type for a taxi ride is a **credit card** since **1** is assigned for credit card payment. It returns **True** for rows where the payment is **1** (credit card), and **False** for all other rows.

Next, ```taxi_data[taxi_data['payment_type'] == 1```, this part filters the ENTIRE dataset ```taxi_data``` to include only rows where payment type is **1** (True). It selects all the rows where customers used credit card to pay.

Finally, after filtering data for ONLY credit card payment, ```['fare_amount']``` extracts the columns that contain the fare amount for the selected rows. It gives you just the fare amounts for rides where the payment was made using a credit card ONLY.

🔁 Similar approach for Cash payment.

```python
stats.ttest_ind(a=credit_card, b=cash, equal_var=False)
```
![p-value](https://github.com/user-attachments/assets/68576db6-f04d-4428-8611-4c9f6fdeca0e)

✍ Proceed with a **two-sample t-test** to compute p-value given 5% as the significant level.

Set ```equal_var=False``` because we don't want the 2 samples have the same variance.

---

**3) Provide insights to stakeholders:** 

**Hypothesis testing:** 

- **NULL hypothesis:** There is **no difference** in the average fare amount between customers who use credit cards and customers who use cash.

- **ALTERNATIVE hypothesis:** There is **a difference** in the average fare amount between customers who use credit cards and customers who use cash.

✍ Result shows **p-value is extremely small, significantly less than the 5% signigicant level.** Thus, we can confidently **reject the NULL hypothesis**, meaning there is a difference in the average fare amount between customers who use credit cards and customers who use cash. Furthermore, drivers can increase revenue by **encouraging customers to pay with credit card** instead of cash. 


# Case Study 2: TikTok 🎵
## Link here: [Case_study_2: TikTok](https://github.com/amy941/Google_Advanced_Module-4_Statistics/blob/main/Case_Study_2_TikTok.ipynb)

## Scenario: 
TikTok is working on the development of a predictive model that can determine whether a video contains a claim or offers an opinion. TikTok's data team has been asked to investigate TikTok's user claim dataset to determine which hypothesis testing method best serves the data and the claims classification project. Questions to be answered are:

- Do videos from verified accounts and videos unverified accounts have different average view counts?
- Is there a relationship between the account being verified and the associated videos' view counts?
  
By answering these 2 questions, TikTok's data team can discover the patterns in TikTok user claim dataset that could influence or inform the development of the predictive model.

## What I Learned:

**1) Compute a descriptive stats:**
A quick overview of the content and structure of a dataset before proceeding. The following functions are used:

**pandas:** .describe(), .head(), .isna() | **numpy:** .mean()

```python
data.describe(include= 'all')
```
![describe()_tiktok](https://github.com/user-attachments/assets/3ada81fd-1977-4bb2-b4c6-e6ef899a9347)

```python
data.isna().sum()
```
![isna()_tiktok](https://github.com/user-attachments/assets/d2d6a6f3-6cc3-42f4-b438-4adfb13471e0)

✍ Cleaning dataset: *.isna()* stands for **is NaN** (is Not-a-Number, means data is missing). It's used to check and handle missing values in a dataset.


Table shows:
- Columns WITH missing values: value of 298 (means 298 missing values), ```claim_status```, ```video_transcription_text```, etc.
- Columns WITHOUT missing values: value of 0 (means 0 missing value), ```video_id```, ```video_duration_sec```, etc.

```python
data = data.dropna(axis=0)
```
✍ To further clean up the dataset, *.dropna(axis=0)* is used to drop rows with missing values from previous step. Then, we use *.head()* to displace the new set of data after cleaning.

![describe()_after clean_tiktok](https://github.com/user-attachments/assets/17479257-7c52-4b3d-be4c-64a128abbbdf)

Table above shows the finalized dataset after cleaning. 

```python
data.groupby("verified_status")["video_view_count"].mean()
```
![mean()_tiktok](https://github.com/user-attachments/assets/dbf5a15f-33c6-42f6-b406-7a09c35d44ee)

✍ We're intested in the relationship between ```verified_status``` and ```video_view_count```. Use *.groupby()* and *.mean()* to compute the average of **video_view_count** for each group of **verified_status** in the sample data.
The output of the code shows **not_verified_videos has more views than verified_videos,** 265663 views vs. 91439 views, respectively.

---

**2) Conduct Hypothesis test and A/B test:**
```python
# Save each sample in a variable
not_verified = data[data["verified_status"] == "not verified"]["video_view_count"]
verified = data[data["verified_status"] == "verified"]["video_view_count"]

# t-test
stats.ttest_ind(a=not_verified, b=verified, equal_var=False)
```

✍ Similar approach as Case Study 1, 
- First, assigned variables, one for 'not_verified', one for 'verified'
- Then, ```data['verified_status] == "not_verified"``` is used to identify rows where verified_status contains "not verified".
- Next, ```data[data['verified_status] == "not_verified"``` filters the whole dataset. Keep only rows where the condition is ```True```
- Finally, ```[video_view_count]``` is used to extract the video_view_count column from the filtered rows.

🔁 Do the same for "verifed" case.

![p-value_tiktok](https://github.com/user-attachments/assets/075c9797-6d26-43b5-824b-6106231f7a4a)

✍ Proceed with a **two-sample t-test** to compute p-value given 5% as the significant level. After excecuting the code, p-value is (2.61e^-118)%, negligible!

---

**3) Provide insights to stakeholders:** 

**Hypothesis testing:** 

- **NULL hypothesis:** There is **no difference** in number of views between TikTok videos posted by verified accounts vs. TikTok videos posted by unverified accounts

- **ALTERNATIVE hypothesis:** There is **a difference** in number of views between TikTok videos posted by verified accounts vs. TikTok videos posted by unverified accounts .

✍ Result shows **p-value is extremely small, significantly less than the 5% signigicant level.** Thus, we can confidently **reject the NULL hypothesis**, meaning there is a difference in number of views between TikTok videos posted by verified accounts vs. TikTok videos posted by unverified accounts. This issue could cause due to clickbait videos or spam bots that spikes the view counts. 

# Tools I used:
**Python, Jupyter Notebook, GitHub**

# Conclusions:
The end-of-course portfolio projects reinforced my data analysis skills in:
- Importing relevant packages.
- Conducting descriptive summary to explore the project data.
- Implementing hypothesis test and A/B test.
- Interpreting statistical analyses using Python.
- Sharing meaningful insights and ideas with stakeholders.
  
# Closing Thoughts:
Statistics is tough 🙃 It took me over a month to get the hang of the basics (very basic). Regardless, I think I'm in a better place than I was last month 🐌🐌🐌
