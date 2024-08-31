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
## Data Cleansing
### Reading the file
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/bc90ad18-4243-4149-af97-2bbbd6bf99a7)
```
df.isnull()
```

![image](https://github.com/user-attachments/assets/a35e2ed8-6717-456d-969a-df006df96b35)
```
df.notnull()
```
![image](https://github.com/user-attachments/assets/8b6009a5-a48f-439b-a7de-dea6231cb845)
### Removing Null Values
```
# Removes rows with missing values
dfclal=df.dropna(how="all")
print(dfclal)
```
![Screenshot 2024-08-31 141504](https://github.com/user-attachments/assets/d4af0552-529e-472b-95f2-5f2928f8a8b5)
```
# Rows with any one missing value gets deleted
dfclan=df.dropna(how="any")
print(dfclan)
```
![image](https://github.com/user-attachments/assets/2aa75c9e-48af-43d2-a13d-7c7025f05494)


### Filling Null Values
```
dfl=df.fillna(0)
print(dfl)
```
![image](https://github.com/user-attachments/assets/0d89f5e1-526a-4e71-a3c0-af9cfde6ccfc)
```
dflfl=df.fillna(method='ffill')
print(dflfl)
```
![image](https://github.com/user-attachments/assets/635f4444-5c86-4c44-b841-03e96fc6c522)
```
dflbl=df.fillna(method='bfill')
dflbl
```
![image](https://github.com/user-attachments/assets/406a3b36-2fdb-4914-919d-11fcbcf40f5b)
```
dflmn=df.fillna(df['Age'].mean())
dflmn
```
![image](https://github.com/user-attachments/assets/089c9391-2153-41d6-a145-598c6eec7746)
## Outlier Detection and Removal
```
import numpy as np
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
![image](https://github.com/user-attachments/assets/42ae6e31-10a6-4e51-a862-d1c2364a4bbf)
```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/31903278-ee25-4f42-b461-53dc65606b75)
```
sns.boxenplot(data=af)
```
![image](https://github.com/user-attachments/assets/3cc7657e-26c9-452e-aebc-766956e3be72)
```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/1e04328f-c769-4ae3-9ad9-1d5a6183a235)
```
q1=af.quantile(0.25)
q2=af.quantile(0.50)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/5e1dae2a-e819-464f-8068-1ed7bf536f2f)
```
w1=np.percentile(af,25)
w2=np.percentile(af,75)
w3=w2-w1
w3
```
![image](https://github.com/user-attachments/assets/8ab23539-23cd-4798-9474-e5761892fdf9)
```
lowerbound=w1-1.5*w3
Upperbound=w2+1.5*w3
print(lowerbound,Upperbound)
```
![image](https://github.com/user-attachments/assets/2ddd5416-8350-4a99-813a-dd009e516f14)
```
outliers=[x for x in age if x<lowerbound or x>Upperbound]
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/99ad5612-e79f-46e5-8db0-5c0c2e61f1ea)
```
af=af[((af>=lowerbound)&(af<=Upperbound))]
af
```
![image](https://github.com/user-attachments/assets/ac9656c1-1b1b-45e3-b9da-161084224396)
```
af.dropna()
```
![image](https://github.com/user-attachments/assets/1520e00f-9727-49d5-a202-8749bdbe82a8)

```
sns.boxplot(data=af)
```
![image](https://github.com/user-attachments/assets/c6e5db6e-b2b0-4173-add9-941be1e06171)
```
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/0f7aed1c-737e-4f2e-9398-780a0f5c5473)





# Result
          <<include your Result here>>
