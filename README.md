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
data=pd.read_csv("/content/SAMPLEIDS.csv")
```

```
data.head(7)
```

![image](https://github.com/user-attachments/assets/8a9a951f-5d97-40a6-9f66-380b9fce2645)

```
df.isnull()
```

![image](https://github.com/user-attachments/assets/18aae166-eb62-4622-9fd5-416831c5da1c)

```data.isnull().sum()
```

![image](https://github.com/user-attachments/assets/218941a3-2b36-48f9-aa79-c4c7d79b89a3)

```
data.isnull().any()
```

![image](https://github.com/user-attachments/assets/b1d5f83d-9a5e-4519-bb76-86d144f07c62)

```
data.notnull()
```

![image](https://github.com/user-attachments/assets/9713c6e3-59e5-4409-b8d7-2cb637a7d586)

```
data.fillna(0)
```

![image](https://github.com/user-attachments/assets/cedd4c39-3870-4984-9989-4a346223fc81)

```
data.dropna(axis=0)
```

![image](https://github.com/user-attachments/assets/86235767-3313-48d2-a8b9-b38f4b3c4e40)

```
data.dropna(axis=1)
```

![image](https://github.com/user-attachments/assets/3b3cb61f-490b-4ac8-806c-733d34024f6d)

```
data.fillna(method="ffill")
```

![image](https://github.com/user-attachments/assets/9794b534-8b8e-4a66-94fb-e03655d6e33d)

```
data.fillna(method="bfill")
```

![image](https://github.com/user-attachments/assets/3ca3d089-87ba-4e48-a8d7-d0c5a8178320)

```
data_dropped = data.dropna()
data_dropped
```

![image](https://github.com/user-attachments/assets/b11e93a2-ffbe-4d94-a1b4-ad3b4ff8acd9)

```
data.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```

![image](https://github.com/user-attachments/assets/983c7fbe-b154-4fd2-a782-16725854ed2d)

```
data.shape
```

![image](https://github.com/user-attachments/assets/a3293f60-a780-418a-8adc-d8fb454adeee)

```
data.info()
```

![image](https://github.com/user-attachments/assets/9df8efa7-6157-4dd3-a240-b16ca462b0b6)

```
data.describe()
```

![image](https://github.com/user-attachments/assets/986777e5-27fd-4a44-bf73-f033076cce44)

```
ir=pd.read_csv('iris.csv')
ir
```

![image](https://github.com/user-attachments/assets/db918e69-f0ca-4fd1-b1e7-1042b0034563)

```
ir.describe()
```

![image](https://github.com/user-attachments/assets/2a0662b5-a71a-4e9d-ad9c-d21f574269f0)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/32d73f88-81a5-47a0-8328-4a1ef60907be)

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iq=q3-q1
print(q3)
```

![image](https://github.com/user-attachments/assets/ae08af17-1e37-4969-b09d-5d5bded43655)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

![image](https://github.com/user-attachments/assets/d3b10c14-ba5c-4e56-b1f9-1b8f06919c32)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

![image](https://github.com/user-attachments/assets/651c6014-8608-4e6d-98a1-0cb76727d4f1)

```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/user-attachments/assets/77399e11-ab2b-4b7a-9f57-3ad4b5439e99)

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```

![image](https://github.com/user-attachments/assets/810967d1-40bf-43d4-9405-e919e7187562)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/355cdb16-038b-4c9a-8250-161e620f2509)

```
low = q1 - 1.5*iqr
low
```

![image](https://github.com/user-attachments/assets/cc847847-540d-4c72-8802-b8cd5499ddc7)

```
high = q3 + 1.5*iqr
high
```

![image](https://github.com/user-attachments/assets/7f0f29fd-7005-4943-9715-2b8c1ea4c0d8)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![image](https://github.com/user-attachments/assets/8095fc52-21f2-4254-beb6-039c729a2cae)

```
z = np.abs(stats.zscore(df['height']))
z
```

![image](https://github.com/user-attachments/assets/be18dbb1-5f61-4831-96dd-f9b2b08b119c)

```
df1 = df[z<3]
df1
```

![image](https://github.com/user-attachments/assets/48ebe975-18f9-421a-bd10-390b82aea7b5)


# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
