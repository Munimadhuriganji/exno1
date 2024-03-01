# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![Screenshot 2024-02-29 214919](https://github.com/Munimadhuriganji/exno1/assets/138849444/81737556-6f87-498c-991d-c423b870b3c7)

```
data = pd.get_dummies(data)
data.isnull().sum()
```
![Screenshot 2024-02-29 215005](https://github.com/Munimadhuriganji/exno1/assets/138849444/789fa5f2-517a-4230-a125-c1eb51f2be83)

```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![Screenshot 2024-02-29 215014](https://github.com/Munimadhuriganji/exno1/assets/138849444/7654aefb-7069-4b35-b716-d4c5daf6a1d6)

```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
### IOR
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![Screenshot 2024-02-29 215024](https://github.com/Munimadhuriganji/exno1/assets/138849444/52d2b6c3-7b23-4402-9969-f71a7c6c3cd0)

```
ir.describe()
```
![Screenshot 2024-02-29 215031](https://github.com/Munimadhuriganji/exno1/assets/138849444/3de885c5-f831-4177-a7ce-64aa285e618a)

```
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2024-02-29 215039](https://github.com/Munimadhuriganji/exno1/assets/138849444/cc7919b0-a410-4a7b-82b8-2477b3167fb2)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![Screenshot 2024-02-29 215046](https://github.com/Munimadhuriganji/exno1/assets/138849444/c3afb8bb-57f6-4791-a452-93a0e371a242)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![Screenshot 2024-02-29 215053](https://github.com/Munimadhuriganji/exno1/assets/138849444/c3f1d6ce-bdfd-401b-9ea1-c572aa55e10e)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![Screenshot 2024-02-29 215105](https://github.com/Munimadhuriganji/exno1/assets/138849444/d3d2cdc8-c20b-4fd8-b126-23bf2a830a2c)
```
sns.boxplot(x='sepal_width',data=delid)
```
![Screenshot 2024-02-29 215113](https://github.com/Munimadhuriganji/exno1/assets/138849444/95d9df34-3e5a-4323-9807-384f3303d3d6)
### Z Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![Screenshot 2024-02-29 215119](https://github.com/Munimadhuriganji/exno1/assets/138849444/7ebd8b84-4d1e-4c85-8f33-2d113fd007bb)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```


# Result
The data cleaning process is succesfully completed.
