# Exno:1
Data Cleaning Process

 # AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
```
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers
```

# Coding and Output:
# Reading the data set:
```
import pandas as pd
import seaborn as sns
import numpy as np

df=pd.read_csv("SAMPLEIDS.csv")
df
```
# Output:
```
![image](https://github.com/user-attachments/assets/9bcac124-5658-4499-b348-429226e7636a)
```
# Initializing id=column
```
id=df['M4']
id
```
# Output:
```
![image](https://github.com/user-attachments/assets/a7cd3883-0ca2-40b6-bef6-1a366da402cd)
```
# sns graphs
```
![image](https://github.com/user-attachments/assets/3395f1f8-638a-46d8-959a-ef2ca6e31e83)
![image](https://github.com/user-attachments/assets/d1fb3b8c-f308-46bf-8784-7212629cd08e)
![image](https://github.com/user-attachments/assets/25617c87-400c-43c1-a712-3bcabef4392c)
```
# Quantile and IQR:
```
q1=id.quantile(0.25)
q2=id.quantile(0.5)
q3=id.quantile(0.75)
iqr=q3-q1
iqr
```
# Output:
![image](https://github.com/user-attachments/assets/f9ec0a17-cc86-4a68-9e5b-f3417012043b)
# Declaring bounds:
```
lower_bound=q1-1.5*iqr
upper_bound=q3+1.5*iqr
lower_bound,upper_bound
```
# Output:
![image](https://github.com/user-attachments/assets/f9f62c15-0012-43be-96dd-badac2ed3efe)
# Outliers:
```
outliers=[x for x in id if x<lower_bound or x>upper_bound]
print("Outliers:",outliers)
```
# Output:

![image](https://github.com/user-attachments/assets/56d26ec7-eac0-4c95-bc4a-463551c4eea0)
# Dropna function to remove any null values:
```
id.dropna()
```
 # Output:

 ![image](https://github.com/user-attachments/assets/e8cf0b3e-a543-4ab9-917e-d4977989f9b7)

 # Printing all requird values:
```
print("Q1:",q1)
print("Q2:",q2)
print("Q3:",q3)
print("IQR:",iqr)
print("lower_bound:",lower_bound)
print("upper_bound:",upper_bound)
print("Outliers",outliers)
```
# Output:

![image](https://github.com/user-attachments/assets/559eb9a0-7cb8-407b-8c69-f9bf196d4c85)
# Checking for any outliers at the end:
```
sns.boxplot(id)
```
# Output:

![image](https://github.com/user-attachments/assets/a266ea20-010f-4545-9faa-9fccfbfc67b5)
 # Calculating Z_score:
 ```
import scipy.stats as stats
import pandas as pd
import numpy as np


mean = df['M4'].mean()
std_dev = df['M4'].std()

df['z_score'] = (df['M4'] - mean) / std_dev

print(df)

z = np.abs(stats.zscore(df['M4']))
z
```
 # Output:

  # Result
 Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.










