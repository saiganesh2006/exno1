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
![image](https://github.com/user-attachments/assets/32995fa9-e46e-4209-ba33-584cb753e158)

```
df.head()
```
![image](https://github.com/user-attachments/assets/1e935b5b-f81a-4f85-9a9b-3f61b49e51ed)
```
df.tail()
```
![image](https://github.com/user-attachments/assets/30c04c8f-8736-4c54-8355-4a0a47fab466)
```
df.info()
```
![image](https://github.com/user-attachments/assets/690d6af3-023e-4987-8ee1-726067c4a460)
```
df.describe()
```
![image](https://github.com/user-attachments/assets/90825f5c-7aa9-455f-a6c4-e40e8f7a1123)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/975fb6e2-c71b-414a-baf9-bbb7452964de)

```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/eaa9089d-5f51-439b-9e37-6ed8d7a94bff)
```
df.dropna()
```

![image](https://github.com/user-attachments/assets/b7cf905c-3b6c-4b25-9aa8-b0ef17948bd1)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/84fd3283-87c9-43a5-a267-dd6c3c870bd1)

```
df.fillna(method='ffill')
```
![image](https://github.com/user-attachments/assets/c478bbd5-cf09-4d6a-a5ba-a5cff3d5a50c)

```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/8f800194-7fdd-418c-a332-194d9769a3b2)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/4f029be2-5ee0-4192-ac1d-3d4b29f904a4)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/e6d803c7-5d22-43a9-8b1d-96271c7b26dc)

```
ir=pd.read_csv("/content/iris.csv")
ir
```
![image](https://github.com/user-attachments/assets/e707ecde-24a1-4e94-881a-058165e5e98d)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/ea5c6e41-5055-42c5-9f52-87996678a34a)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/d6c28816-241d-46ff-9bbd-8abb71f10c7c)

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```
![image](https://github.com/user-attachments/assets/db2c1105-3b32-471d-b52d-1fd4790e1591)

```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/be4eeae9-b6fd-45f3-b0a9-660286fae719)

```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/6d30b608-9d0a-437f-8d99-88fe6420c814)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/267312d7-fa57-4602-9d69-011dc1a71852)

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/b1f31eb6-75ea-4357-ac35-fdcf2d1637eb)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
![image](https://github.com/user-attachments/assets/891c8892-8131-497f-8bdb-83512901ffb6)

```
low = q1- 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/7620c655-eb34-4bfb-9845-1d1870da7a95)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/f3e3a364-18ff-488a-aa15-b5213da58bd5)


```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/5dafb554-1a8d-4776-9989-e6fc3e74183d)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/13473059-e750-4abf-8cc9-598cdccef64b)


```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/63d61b39-9b4a-4909-bb8c-98751896a746)

## Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
