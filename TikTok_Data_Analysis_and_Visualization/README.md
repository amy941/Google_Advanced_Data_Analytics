
# OVERVIEW:

# Case Study: TikTok 🎵
## Link here: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Data_Analysis_and_Visualization/Case%20Study_%20TikTok%20.ipynb)
                                   

## Scenario:
The TikTok data team aims to develop a machine learning model to classify claims from user submissions, requiring data analysis and preparation before model building. At this stage, they performed exploratory data analysis (EDA) to understand how videos impact users. The analysis focused on key engagement metrics like view count, like count, comment count, etc.

---


# PACE: Plan 📝
### **Task 1) Imports, Links, and Loading:**

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

```python
data = pd.read_csv("tiktok_dataset.csv")
```

✍️ Library/package:

**- NumPy:** for *vector and matrix computations.*

**- Pandas:** for manipulating and analyzing *tabular data.*

**- matplotlib and seaborn:** to create *graphs, charts, and other data viz.*

  
---

# PACE: Analyze 🔎
### **Task 2) Inspect the data:**

- ```.head()```, ```.size```, ```.shape```

✍️ ```.head()```: **display the first few rows** of the df.

```.size```: **# of rows multiple by # of columns** in a df.
    
```.shape```: an attribute in Python, will output **the dimension** of a dataset as: ([rows] , [columns])

      
- ```.info()```, ```.describe()```

✍️ ```.info()```: provide **total number of rows** (19,382) **and columns** (12), also state the **names and data types** of each column and **the size** of the df.

![info](https://github.com/user-attachments/assets/f5dbec7e-7abc-4049-9078-998dddcc4c92)

✍️ ```.describe()```: generate a table of **descriptive stats.**

![describe](https://github.com/user-attachments/assets/c46d41a5-2ece-45aa-978e-5a906d545180)

🔴 **Things should notice:**
  
* video_duration_sec: max = 60
* video_view_count: max = ~1,000,000 (1e6)
* video_like_count: max = ~660,000
* video_share_count: max = ~260,000
* video_download_count: max = ~15,000
* video_comment_count: max = ~10,000

⚠️⚠️⚠️ For more details, visit: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Data_Analysis_and_Visualization/Case%20Study_%20TikTok%20.ipynb)

---

# PACE: Construct 📊
### **Task 3) Build visualizations:**

Create a **BOX PLOT** and **HISTOGRAM** to examine columns of ```count``` variables (ex: video_duration_sec, video_view_count, video_like_count,...)

```python
plt.figure(figsize=(7,1))
plt.title('video_duration_sec')

sns.boxplot(x=data['video_duration_sec'])

plt.show()
```
![boxplot_1](https://github.com/user-attachments/assets/f314421d-b487-4be6-a8b6-d62e1ee8e31b)


✍️ ```sns.boxplot(x=data['video_duration_sec'])```: *sns.boxplot()* function takes positional argument of x, representing the x-axis in the data. The x-axis will represent the ```video_duration_sec``` column from the df. 

🔁 Write similar code blocks for ```video_view_count```, ```video_like_count```, ```video_comment_count```, ```video_share_count```, ```video_download_count```. The rest of my work: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Data_Analysis_and_Visualization/Case%20Study_%20TikTok%20.ipynb)

```python
plt.figure(figsize=(5,3))
plt.title('video duration sec_HISTOGRAM')

sns.histplot(data['video_duration_sec'], bins=range(0, 61, 5))  #start, stop, step

plt.show()
```

![hist_1](https://github.com/user-attachments/assets/55e7094f-dfec-410f-973e-b9beb0a779a0)

✍️ ```sns.histplot(x, bins, binrange, binwidth, ...)```: to generate a histogram in seaborn.
- **x:** a sequence of values representing the data you want to plot.
- **bins:** ```bins=range(0, 61, 5)``` defines the x-axis starts from 0, stops at 61, and increments by 5.

🔁 Write similar code blocks for ```video_view_count```, ```video_comment_count```, ```video_share_count```, ```video_download_count```

⚠️⚠️⚠️ For more details, visit: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Data_Analysis_and_Visualization/Case%20Study_%20TikTok%20.ipynb)

```python
plt.figure(figsize=(5,3))
plt.title('video like count_HISTOGRAM')

# Create histogram
ax = sns.histplot(data['video_like_count'], bins=range(0, (7 * 10**5 + 1), 10**5))

# Set x-tick positions
xticks = range(0, 7 * 10**5 + 1, 10**5)
ax.set_xticks(xticks)

# Set x-tick labels
labels = [str(i) + 'k' for i in range(0, 701, 100)]  # Adjust this to match the number of ticks
ax.set_xticklabels(labels)

plt.show()
```

![hist_2](https://github.com/user-attachments/assets/3b148851-e005-482d-9d44-745eb1a8437d)

✍️ ```sns.histplot(data['video_like_count'], bins=range(0, (7 * 10**5 + 1), 10**5))```: As we observed in the summary table for descriptive stats in step 2, the maximum of ```video_like_count``` is around 660,000 likes. Thus, we have to customize the bin range and bin width accordingly.
- Start from 0 up to 700,000
- Stops at 7*(10^5) + 1 = 700,001 = 700K
- A step of 10^5= 100,000 = 100K

✍️ ```labels = [str(i) + 'k' for i in range(0, 701, 100)] ```: use for loops to iterate over ```range(0,701,100)``` (start from 0 to 701 in steps of 100). Each number ``i``` is converted into a string and ```k``` is added to show values in a more readable way (ex: 100k instead of 100,000).

⚠️⚠️⚠️ For more details, visit: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Data_Analysis_and_Visualization/Case%20Study_%20TikTok%20.ipynb)

-----
**Create HISTOGRAM for claim status**

- Claim status by verification status
- Claim status by author ban status
- Median view counts by ban status

**Median view counts by ban status**: create a **bar plot** with 3 bars: one for each author ban status (active, under review, banned). The height of each bar should correspond with the **MEDIAN** number of views for all videos with that author ban status.

```python
ban_status_counts = data.groupby(['author_ban_status']).median(numeric_only=True).reset_index()

plt.figure(figsize=(5,3))
plt.title('Median view count by ban status')

sns.barplot(data=ban_status_counts,
             x= 'author_ban_status',
             y= 'video_view_count',
             order= ['active', 'under review', 'banned'],
             palette= {'active':'green', 'under review':'orange', 'banned':'red'},
             alpha= 0.5
)

plt.show()
```

![bar_median](https://github.com/user-attachments/assets/08952775-bc8b-445b-928a-56de1008105a)


✍️ ```ban_status_counts = data.groupby(['author_ban_status']).median(numeric_only=True).reset_index()```

- First, using **.groupby()** function to combine all rows with the same data into a single row. In this case, we only care for ```author_ban_status``` column, with 3 statuses: active, under review, and banned.
  
- Next, using **.median(numeric_only=True)** to compute the median (middle value) for all numeric columns within each group. The argument ```numeric_only=True``` ensures that only numeric columns are captured, ignoring non-numeric values like strings
  
- Finally, using **.reset_index()** positions ```author_ban_status``` as regular column instead of an index, making the dataframe easier to work with.
  

✍️ ```sns.barplot(....)```: 

- First, using **sns.barplot()** to plot a bar graph from seaborn package.

- Then, **define the dataframe** that contains the data for the plot, ```data=ban_status_counts,```

- Next:

**set the x-axis** to represent the ```author_ban_status``` column which has 3 categories: 'active', 'under review', and 'banned'.

**set the y-axis** to display values from ```video_view_count``` column which contains median view counts per each ban status ('active', 'under review', 'banned')

**order=[]** and **palette={}** to define the order and custom colors for each category.

**alpha=0.5** to set the transparency of the bar. 0 is fully transparent, 0.5 is semi-transparent, and 1 is fully opaque.


⚠️⚠️⚠️ For more details, visit: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Data_Analysis_and_Visualization/Case%20Study_%20TikTok%20.ipynb)


---
### **Task 4) Determine Outliers**

```python
count_cols = ['video_view_count',
              'video_like_count',
              'video_share_count',
              'video_download_count',
              'video_comment_count',
              ]

for column in count_cols:
    q1 = data[column].quantile(0.25)
    q3 = data[column].quantile(0.75)
    iqr = q3 - q1
    median = data[column].median()
    outlier_threshold = median + 1.5*iqr

    # Count the number of values that exceed the outlier threshold
    outlier_count = (data[column] > outlier_threshold).sum()
    print(f'Number of outliers, {column}:', outlier_count)
```
![outliers](https://github.com/user-attachments/assets/2f038c47-42de-4f51-aff3-6a510dcc6745)

✍️
- Create a **for loop** to iterate over the column names of each count variable.
  
- **25th percentile (Q1)** and **75th percentile (Q2)** of count variables were determined.
  
- Take the difference between Q1 and Q2 to find the **interquartile range (IQR)**

- Calculate the **median** of the column, then find the **outlier threshold** =(median + 1.5*IQR)

- Count the number of values that **exceed the outlier threshold** then print the output values.


**Scatterplot**

```python
sns.scatterplot(x=data["video_view_count"], 
                y=data["video_like_count"],
                hue=data["claim_status"], 
                s=10, 
                alpha=0.3)

plt.show()
```
![scatterplot](https://github.com/user-attachments/assets/f991bcd1-fd0a-4e80-9047-1748d2862c6e)

⚠️⚠️⚠️ For more details, visit: [Case Study: TikTok](https://github.com/amy941/Google_Advanced_Data_Analytics/blob/main/TikTok_Data_Analysis_and_Visualization/Case%20Study_%20TikTok%20.ipynb)

---
# PACE: Execute 🤝

**- Results and Evaluation:**
  
  * In task 3 - Building visualizations: We explored **the spread** of values and **the distribution** for each ```count``` variable. Most of ```count``` variables are **skewed to the right** (except for ```video_duration_sec``` which resulted in a normal distribution).
    
  * Also in task 3, after investigating **the median view counts by ban status,** we noticed the median view counts for non-active authors are much greater than the median view counts for active authors. Since under review/banned authors are more likely to post claims, thus, their videos attract more views.

  * In task 4 - Determine Outliers: Because the values for the ```count``` variables are heavily skewed to the right as we examined in Task 3, defining an outlier by calculating the interquartile range (IQR) and setting a threshold that of 1.5 * IQR above the 3rd quartile was the best approach.
 

**- Conclusions:** 

  * Exploratory Data Analysis (EDA) helps a data professional to get to know the data, understand its outliers, clean its missing values, and prepare it for future modeling.

  * Data viz helps me understand that we will need to make decisions on certain considerations before designing a model.

---
# CERTIFICATE

![cert](https://github.com/user-attachments/assets/9b2c66c0-3512-4f07-b935-1ace387e5e38)
