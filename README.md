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
import pandas as pd
df=pd.read_csv("/content/Data_set.csv")
df
df.head()
df.tail()
df.isnull()
df.describe()
df.dropna(axis=1)
df.dropna(axis=0)
df.fillna(0)
![Screenshot 2024-02-29 081936](https://github.com/DHINESH-SEC/exno1/assets/138849444/46cd76e7-16a0-481d-9227-6eebae384171)


import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
![Screenshot 2024-02-29 081947](https://github.com/DHINESH-SEC/exno1/assets/138849444/98d271b2-93ac-4ff9-9ec9-f72f16d521a6)


import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1

low=q1-1.5*iqr
low
![Screenshot 2024-02-29 081956](https://github.com/DHINESH-SEC/exno1/assets/138849444/2c888748-8868-445e-b6ae-299806edfbf0)

high=q3+1.5*iqr
high
![Screenshot 2024-02-29 082001](https://github.com/DHINESH-SEC/exno1/assets/138849444/e41badfa-f5c2-4982-a9db-5753078c5cf0)

aq=af[((af>=low)&(af<=high))]
aq.dropna()
![Screenshot 2024-02-29 082028](https://github.com/DHINESH-SEC/exno1/assets/138849444/0b2921d7-f39d-4d77-a82a-8becd4282e6e)


af=af[((af>=low)&(af<=high))]
af.dropna()
![Screenshot 2024-02-29 082028](https://github.com/DHINESH-SEC/exno1/assets/138849444/0b2921d7-f39d-4d77-a82a-8becd4282e6e)

# Result
to perform data cleaning and save the cleaned data to a file is suceesfully completed.
