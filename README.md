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
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/832f8cad-7e0d-4bca-b184-e3b18a91523d)

```
df.isnull().sum()
```
![Screenshot 2024-08-17 104837](https://github.com/user-attachments/assets/61b0037e-678d-4435-a030-2682cbea43e0)

```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/2e22e4e9-5d78-45d0-a044-46468ff61c51)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/9fb39c42-db7d-4317-b2ac-a99f014d610b)

```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/d6fadaca-3881-485d-89b3-99f2e09b83b7)

```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/be1a695c-112d-43a0-afc7-65cd65aeeec3)

```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/1e3ab028-60cf-4fc3-adf3-8ee9f14ddd52)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/07b184ac-06e1-4a3e-9070-50fe79725101)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/0240281f-1e57-4ec0-b7dd-feb388fc0097)


```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/1c18c241-2b59-4575-98a3-11a23733bd6e)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/1571773c-a38f-44b4-ba54-879c22856204)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/3cd581df-2d9b-46cd-b9c5-c42f3a165737)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/3933313c-cde5-445d-9558-06f61f0678e2)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/0337a47e-18e1-4936-beb4-c8663f9777d8)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/eb7584e4-db54-428c-880d-2a2a276bcda6)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/431ab83b-33d5-48e9-8550-fd05a4844ea4)

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/ba5ad35a-3e95-4643-bf02-e868069c35cd)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/cda855ec-74b8-47ff-acba-d0986423fb4a)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/506eb567-b7d5-43ed-9664-220743ab2622)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/4fae0238-dfa4-415b-b4f4-2e3fb9120a5e)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/663adad8-8315-45e1-bd3c-8a3e3ed1dfd7)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/12c50cca-4e06-4cb0-8105-8147e5730721)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/04774b9b-cb6c-4058-86f8-1a5fdeeaa012)

          
            
# Result
         Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
