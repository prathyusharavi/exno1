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
image

Initializing id=column
id=df['M4']
id
 # Output:
image

sns graphs:
image image image

Quantile and IQR:
q1=id.quantile(0.25)
q2=id.quantile(0.5)
q3=id.quantile(0.75)
iqr=q3-q1
iqr
# Output:
image

Declaring bounds:
lower_bound=q1-1.5*iqr
upper_bound=q3+1.5*iqr
lower_bound,upper_bound
 # Output:
image

Outliers:
outliers=[x for x in id if x<lower_bound or x>upper_bound]
print("Outliers:",outliers)
Output:
image

Dropna function to remove any null values:
id.dropna()

 # Output:
image

Printing all requird values:
print("Q1:",q1)
print("Q2:",q2)
print("Q3:",q3)
print("IQR:",iqr)
print("lower_bound:",lower_bound)
print("upper_bound:",upper_bound)
print("Outliers",outliers)
Output:
image

Checking for any outliers at the end:
sns.boxplot(id)

 # Output:
image

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
image

# Result:
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
