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
Reading the data set:
import pandas as pd
import seaborn as sns
import numpy as np

df=pd.read_csv("SAMPLEIDS.csv")
df
 # Output:
![image](https://github.com/user-attachments/assets/080cac79-16d0-4b68-9cbd-263387a95cbf)

Initializing id=column
id=df['M4']
id
 # Output:
![image](https://github.com/user-attachments/assets/12bae2c1-cdc4-42e0-82a0-1e5f25d6ef07)

sns graphs:
![image](https://github.com/user-attachments/assets/83357ba8-18fb-47e9-b8ce-83f908485c5e)
![image](https://github.com/user-attachments/assets/7e249fed-5258-429c-a736-97e1ef9e8660)
![image](https://github.com/user-attachments/assets/24a57362-0894-418c-8c0c-ffb635d81449)


Quantile and IQR:
q1=id.quantile(0.25)
q2=id.quantile(0.5)
q3=id.quantile(0.75)
iqr=q3-q1
iqr
# Output:
![image](https://github.com/user-attachments/assets/4278fa52-3c0f-4180-b9cb-866c3f064806)

Declaring bounds:
lower_bound=q1-1.5*iqr
upper_bound=q3+1.5*iqr
lower_bound,upper_bound
 # Output:
![image](https://github.com/user-attachments/assets/a366c583-19e3-4ea8-96df-86ba6d05fa20)


Outliers:
outliers=[x for x in id if x<lower_bound or x>upper_bound]
print("Outliers:",outliers)
Output:
image

Dropna function to remove any null values:
id.dropna()

 # Output:
![image](https://github.com/user-attachments/assets/362833e2-71ec-4f70-86d0-583968e8484b)


Printing all requird values:
print("Q1:",q1)
print("Q2:",q2)
print("Q3:",q3)
print("IQR:",iqr)
print("lower_bound:",lower_bound)
print("upper_bound:",upper_bound)
print("Outliers",outliers)
Output:
![image](https://github.com/user-attachments/assets/9209edce-0f87-4edc-8a38-f784b09ac249)


Checking for any outliers at the end:
sns.boxplot(id)

 # Output:
![image](https://github.com/user-attachments/assets/e4c8be4c-abff-499b-ae39-7c04aed632c3)

Calculating Z_score:
import scipy.stats as stats
import pandas as pd
import numpy as np


mean = df['M4'].mean()
std_dev = df['M4'].std()

df['z_score'] = (df['M4'] - mean) / std_dev

print(df)

z = np.abs(stats.zscore(df['M4']))
z
 # Output:
![image](https://github.com/user-attachments/assets/4ce4972f-abba-40c3-b096-05ca8d7c59d0)


# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
