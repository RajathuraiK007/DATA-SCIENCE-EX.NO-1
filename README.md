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
df=pd.read_csv("C:\\Users\\G.POORNIMA DEVI\\Downloads\\Data_set.csv")
df.head()
```

<img width="1516" height="386" alt="image" src="https://github.com/user-attachments/assets/a8277ba5-63da-4e80-be59-8145794f0546" />

```
df.tail()
```

<img width="1491" height="388" alt="image" src="https://github.com/user-attachments/assets/4ec2cd30-2b0b-4176-b8c1-9c29629fcb44" />

```
df.info()
```

<img width="1511" height="502" alt="image" src="https://github.com/user-attachments/assets/f55e6b19-f8b4-4cd0-bacf-d4d4688ed05a" />

```
df.describe()
```

<img width="1574" height="499" alt="image" src="https://github.com/user-attachments/assets/73ad5d6f-ec69-4f40-b770-4693ec298ed5" />

```
print(df.shape)
print(df.columns)
```

<img width="1119" height="318" alt="image" src="https://github.com/user-attachments/assets/efb7b75b-cfb0-4ab9-9ec2-5bed08871d11" />

```
df.dropna(inplace=True)
df
```

<img width="1484" height="780" alt="image" src="https://github.com/user-attachments/assets/42dc525b-039b-48a6-91cd-04b90b9ff569" />

```
import pandas as pd
df=pd.read_csv("C:\\Users\\G.POORNIMA DEVI\\Downloads\\Data_set.csv")
df.dropna(inplace=True)
#IQR
Q1=df['watchers'].quantile(.25)
Q2=df['watchers'].quantile(.50)
Q3=df['watchers'].quantile(.75)
IQR=Q3-Q1
outliers=[]
for i in df['watchers']:
    if i > Q3+1.5*IQR or i < Q1-1.5*IQR:
        outliers.append(i)
print("Outliers are ",outliers)
```

<img width="1483" height="342" alt="image" src="https://github.com/user-attachments/assets/cb77c52c-c379-463f-bf2d-942ec7c997e2" />

```
import pandas as pd
import numpy as np
df=pd.read_csv("C:\\Users\\G.POORNIMA DEVI\\Downloads\\Data_set.csv")
df.dropna(inplace=True)
#Z-Score
X_mean=df['watchers'].mean()
SD=df['watchers'].std()
Z_score=[]
for i in df['watchers']:
    Z_score.append((i-X_mean)/SD)
outliers=[]
Z_score_critical=[]
for i in range(len(Z_score)):
    if Z_score[i]>2.5:
        outliers.append(df['watchers'].iloc[i])
        Z_score_critical.append(Z_score[i])
outliers=[x.item() for x in outliers]
Z_score_critical=[x.item() for x in Z_score_critical]
print("Outliers are", outliers)
print("And their respective Z-scores are",Z_score_critical)
```

<img width="1475" height="514" alt="image" src="https://github.com/user-attachments/assets/0dc3fa37-4cd2-41a7-8f41-ec056c17fc3a" />

# Result
The given data is read and data cleaning is successfully performed and saved the cleaned data in a file. Outliers detection using IQR and Z score methods are successfully performed.
