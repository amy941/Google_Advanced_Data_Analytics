# OVERVIEW:
Built a dataframe for the TikTok dataset using Python packages - **NumPy and Pandas** 

# Case Study 1: TikTok 🎵
## Link here: [Case_study_1: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Claims_with_Python/Case%20Study%202_TikTok.ipynb)

## Scenario: 
Constructing a dataframe in Python for data learning, future Exploratory Data Analysis (EDA), and statistical activities.

## What I Learned:
**1) Imports and data loading:**
```python
import numpy as np
import pandas as pd
```

```python
data = pd.read_csv("tiktok_dataset.csv")
```
✍️ Importing NumPy and Panda packages, then load dataset from CSV file to a dataframe.

---
**2) Inspect the data:**
```python
data.head(10)
data.info()
data.describe()
```

![head](https://github.com/user-attachments/assets/2cd35f16-0df7-4e29-91d3-47b806035dbb)

✍️ *.head()* is used to display a few first rows of df. Reviewing the first few rows, we can tell **df contains different data types (str, int, floats).** Each row represents a distinct TikTok video with comments and statuses. 


![info](https://github.com/user-attachments/assets/9ba3e14c-641b-43e9-ba3d-bf57c202ba88)

✍️ *.info()* is for summary info. The output shows df contains **5 floats, 3 integers, and 4 objects.** Total video counts is **19382 videos**. There are some **missing values** in variables as ```claim_status```, ```video_transcription_text```, and all ```count``` variables.


![describe](https://github.com/user-attachments/assets/722d0424-2c24-439c-942b-420d9ef593fa)

✍️ *.describe()* is for descriptive statistics summary. **Many 'count' variables have outliers.**

---
**3) Investigate the variables:**

```python
claims = data[data['claim_status'] == 'claim']

print('MEAN view count claims: ', claims['video_view_count'].mean())
print('MEDIAN view count claims: ', claims['video_view_count'].median())
```

![claims](https://github.com/user-attachments/assets/a20b9e27-921d-439b-bed4-0e867ed532e3)

✍️ First, examine the amount of videos for each different claim status (claims vs. opinions).
Next, create **BOOLEAN masking** to *filter* the data according to claim status, then determine **MEAN** and **MEDIAN** view counts for each claim status. 

**- Step 1:** Assign a **dataframe** called ```claims```.

**- Step 2:** Write a logical statement: ```data['claim_status'] == 'claim'``` The objective is to keep status as **claim** only and filter out the rest. This is called **BOOLEAN MASKING**. The output will result in **True or False** value in a **Series** object. To apply this mask to dataframe, simply insert this statement into **selector brackets [ ]** and apply it to dataframe, like this: ```data[data['claim_status'] == 'claim']```

**- Step 3:** After filtering df to include only the ```claims```, output the statistical values using *.mean()* and *.median()* method.
  
🔁 Repeat the same steps for ```opinions``` status.

```python
opinions = data[data['claim_status'] == 'opinion']

print('MEAN view count opinions: ', opinions['video_view_count'].mean())
print('MEDIAN view count opinions: ', opinions['video_view_count'].median())
```

![opinion](https://github.com/user-attachments/assets/81339a9e-9a30-4257-9621-0fd1eac5efdd)

---
**4) Grouping and Aggregation:**

```python
data.groupby(['claim_status', 'author_ban_status']).agg({
    'likes_per_view': ['count', 'mean', 'median'],
    'comments_per_view': ['count', 'mean', 'median'],
    'shares_per_view': ['count', 'mean', 'median']
})
```

![groupby](https://github.com/user-attachments/assets/f162d39b-b164-42b3-b6fc-c954f62be196)

✍️ **groupby()** was called directly on df. The data was grouped first by ```'claim_status'```, then by ```'author_ban_status'```. Then, the **agg()** function was applied to calculate the **count**, **mean**, and **median** for the three newly created columns: ```likes_per_view```, ```comments_per_view```, and ```shares_per_view```.

⚠️⚠️⚠️ Check my work for further details about the earlier steps: [Case_study_1: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Claims_with_Python/Case%20Study%202_TikTok.ipynb)

---
# Case Study 2: Automatidata 🚕
## Link here: [Case_study_2: Automatidata](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Claims_with_Python/Case%20Study%201_Automatidata.ipynb)

---
# CERTIFICATE

![cert](https://github.com/user-attachments/assets/f94aa90b-73cc-40a3-913c-295ec7d05d51)
